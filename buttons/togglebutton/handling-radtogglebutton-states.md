---
title: Handling RadToggleButton States
page_title: Handling RadToggleButton States
description: Handling RadToggleButton States
slug: buttons-togglebutton-handling-radtogglebutton-states
tags: handling,radtogglebutton,states
published: True
position: 0
---

# Handling RadToggleButton States



## Properties

The __ToggleState__ property is responsible for getting or setting the state of RadToggleButton.
        

## Events

You can handle the __ToggleStateChanged__ event of __RadToggleButton__to take action when the user toggles the button. The event handler is passed a
          __StateChangedEventArgs__ parameter that includes a __ToggleState__
          member.
        

#### __[C#] Handling the ToggleStateChanged event__

{{region handlingToggleStateChanged}}
	
	        void radToggleButton1_ToggleStateChanged(object sender, StateChangedEventArgs args)
	        {
	            MessageBox.Show(args.ToggleState.ToString());
	        }
	
	{{endregion}}



#### __[VB.NET] Handling the ToggleStateChanged event__

{{region handlingToggleStateChanged}}
	
	    Private Sub radToggleButton1_ToggleStateChanged(ByVal sender As Object, ByVal args As Telerik.WinControls.UI.StateChangedEventArgs)
	        MessageBox.Show(args.ToggleState.ToString())
	    End Sub
	
	{{endregion}}



You can also handle the __ToggleStateChanging__ event. This event
          provides an opportunity to cancel the toggle state change. The __StateChangingEventArgs__
          passed as a parameter to the event handler have __NewValue__ and
          __OldValue____ToggleState__ members and a
          Boolean __Cancel__ member. __NewValue__ holds
          the value of __ToggleState__ that will be applied when the event is
          completed without being canceled. __OldValue__ holds the value of
          __ToggleState__ at the time the state change was initiated.
          __Cancel__ controls which value of __ToggleState__ is
          applied when the event completes. The default is __false__.
          Setting __Canceled__ to __true__ will prevent
          __ToggleStateChanged__ from firing and will leave the
          __ToggleState__ value as it was prior to the event.
        

The example below allows a __RadToggleButton__to toggle only
          when a second __RadToggleButton__is off. If the second button toggle
          state is __On__ and the __NewValue__ is __On__,
          then the toggle is canceled. The __ToggleStateChanged__event only fires
          and changes the __Text__property when __ToggleStateChangiing__does not cancel.
        

#### __[C#] Handling the ToggleStateChanging event__

{{region handlingToggleStateChanging}}
	
	        private void radToggleButton2_ToggleStateChanging(object sender,
	           Telerik.WinControls.UI.StateChangingEventArgs args)
	        {
	            bool attemptingOn = args.NewValue ==
	                Telerik.WinControls.Enumerations.ToggleState.On;
	            args.Cancel = true;
	        }
	
	        private void radToggleButton2_ToggleStateChanged(object sender,
	           Telerik.WinControls.UI.StateChangedEventArgs args)
	        {
	            radToggleButton1.Text = args.ToggleState.ToString();
	        }
	
	{{endregion}}



#### __[VB.NET] Handling the ToggleStateChanging event__

{{region handlingToggleStateChanging}}
	
	    Private Sub radToggleButton2_ToggleStateChanging(ByVal sender As Object, ByVal args As Telerik.WinControls.UI.StateChangingEventArgs)
	        args.Cancel = True
	    End Sub
	
	    Private Sub radToggleButton2_ToggleStateChanged(ByVal sender As Object, ByVal args As Telerik.WinControls.UI.StateChangedEventArgs)
	        radToggleButton1.Text = args.ToggleState.ToString()
	    End Sub
	
	{{endregion}}



>Due to the specifics of the
            [simple data binding](http://msdn.microsoft.com/en-us/library/system.windows.forms.binding(v=vs.110).aspx)

            we have introduced the __CheckChanging__ / __CheckChanged__ events together with the __CheckState__ property.
            These events and property provide the same functionality as the __ToggleStateChanged__, __ToggleStateChanging__ and the
            __ToggleState__ property, but give you the ability to simple data bind the control.
          