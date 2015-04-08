---
title: Starting the Control Spy
page_title: Starting the Control Spy
description: Starting the Control Spy
slug: tools-controlspy-starting-the-control-spy
tags: starting,the,control,spy
published: True
position: 1
---

# Starting the Control Spy



## 

To start the Control Spy, create and display a new instance of the __RadControlSpyForm__contained in the Control Spy library:

#### __[C#] Using RadControlSpy__

{{region usingRadControlSpy}}
	        private void radButton1_Click(object sender, EventArgs e)
	        {
	            RadControlSpyForm spyForm = new RadControlSpyForm();
	            spyForm.Show();
	        }
	{{endregion}}



#### __[VB.NET] Using RadControlSpy__

{{region usingRadControlSpy}}
	    Private Sub RadButton1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles RadButton1.Click
	        Dim spyForm As New RadControlSpyForm()
	        spyForm.Show()
	    End Sub
	{{endregion}}

