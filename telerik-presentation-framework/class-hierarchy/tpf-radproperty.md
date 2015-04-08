---
title: RadProperty
page_title: RadProperty
description: RadProperty
slug: tpf-class-hierarchy-radproperty
tags: radproperty
published: True
position: 2
---

# RadProperty



## 

RadProperty encapsulates properties used in RadObject and support [dependency properties]({%slug tpf-dependency-properties%}). Each RadProperty has a name, type, owner and [metadata]({%slug tpf-class-hierarchy-radproperty-metadata%}), i.e. information about the property. Each RadProperty has mechanisms for synchronizing with other properties in the system and for validating itself.

The RadProperty __AddOwner()__ method associates the owner's type and potentially merges the owners metadata. 

The static RadProperty __Register()__ method creates an instance of a RadProperty and is used to make the property known to TPF. Typically the property is then wrapped in a standard CLR style property as a convenience. In the wrapper property, RadObject methods __GetValue()__ and __SetValue()__communicate with TPF. The example below shows a "phone" property being registered, and then being wrapped as a standard CLR string property. Note: The standard naming convention for dependency properties is <Property name> + "Property".

#### __[C#]__

{{region RadProperty}}
	        public static RadProperty PhoneProperty = RadProperty.Register(
	            "Phone",
	            typeof(string),
	            typeof(BusinessCardElement),
	            new RadElementPropertyMetadata("", ElementPropertyOptions.None));
	
	        public string Phone
	        {
	            get
	            {
	                return (string)this.GetValue(PhoneProperty);
	            }
	            set
	            {
	                this.SetValue(PhoneProperty, value);
	            }
	        }
	{{endregion}}



#### __[VB]__

{{region RadProperty}}
	    Public Shared PhoneProperty As RadProperty = RadProperty.Register("Phone", GetType(String), GetType(BusinessCardElement), New RadElementPropertyMetadata("", ElementPropertyOptions.None))
	
	    Public Property Phone() As String
	        Get
	            Return DirectCast(Me.GetValue(PhoneProperty), String)
	        End Get
	        Set(value As String)
	            Me.SetValue(PhoneProperty, value)
	        End Set
	    End Property
	#End Region
	End Class

