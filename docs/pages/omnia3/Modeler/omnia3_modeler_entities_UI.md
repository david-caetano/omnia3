---
title: Modeling Entities (UI)
keywords: omnia3
summary: "Modeling Entities (UI)"
sidebar: omnia3_sidebar
permalink: omnia3_modeler_entities_ui.html
folder: omnia3
---

## 1. User Interface
__*Entity / User Interface*__

In **OMNIA Platform** you can customize how the fields are shown in the form to create or edit of your entity.

Automatically, the platform adds and removes user interface elements when a new attribute is added or an existing one is deleted from an entity.

The form layout is organized with _Rows_ and _Columns_. Each row is divided horizontally in 12 columns.

### How to add a new element?
By selecting the option _Add new element_ you will be able to add new elements to the layout, after filling the following information:

* **Name**: the entity attribute this element will represent in the layout (will allow you to read and write in this attribute);
* **Label**: the element caption;
* **Help text**: the detailed description of the element;
* **Row**: the layout row in which the element will be placed;
* **Column**: the layout column in which the element will be placed;
* **Size**: the element size on a scale of 1 (the smaller size) to 12 (the bigger size);
* **Is the element hidden?**: the visibility of the element (hidden or visible);
* **Minimal visible screen size**: the visibility of the element, related to the user's device screen size (at sizes smaller than the one selected, the element will be hidden);

### How to add a new container element?
By selecting the option _Add new container_ you will be able to add new containers to your layout, after filling the following information:

* **Name**: the element's unique identifier attribute;
* **Label**: the element caption;
* **Help text**: the detailed description of the element;
* **Row**: the layout row in which the element will be placed;
* **Column**: the layout column in which the element will be placed;
* **Size**: the element size on a scale of 1 (the smaller size) to 12 (the bigger size);
* **Is the element hidden?**: the visibility of the element (hidden or visible);
* **Minimal visible screen size**: the visibility of the element, related to the user's device screen size (at sizes smaller than the one selected, the element will be hidden);

### How to add a new calendar element?
By selecting the option _Add new calendar_ you will be able to add new calendars to your layout, after filling the following information:

* **Name**: the element's unique identifier attribute;
* **Mapping**: the element, of type colection, that will be used as a data source;
(In case of a single date event, use the Date Mapping option, if you require a date interval, use Start and Finish Date Mapping instead)
* **Date Mapping**: the coleciton element that will represent the calendar's event date;
* **Start Date Mapping**: start date of the date mapping;
* **Finish Date Mapping**: end date of the date mapping;
* **Title Mapping**: the element that will be used to define the title property;
* **Category Mapping**: the element that will be used to define the category property;
* **Label**: the element caption;
* **Help text**: the detailed description of the element;
* **Row**: the layout row in which the element will be placed;
* **Column**: the layout column in which the element will be placed;
* **Size**: the element size on a scale of 1 (the smaller size) to 12 (the bigger size);
* **Is the element hidden?**: the visibility of the element (hidden or visible);
* **Minimal visible screen size**: the visibility of the element, related to the user's device screen size (at sizes smaller than the one selected, the element will be hidden);


### How to change the positioning of an element?
In the User Interface tab, select the element you want to change and, in the _Row_ and/or _Column_ fields, set the new positioning values.

### How to change the size of an element?
In the User Interface tab, select the element you want to change and, in the _Size_ field, select the new size.

### How to remove an element?
Picking the element you want to remove, select the option _Delete_ and confirm your option in the confirmation window.

## 2. User Interface Behaviours
__*Entity / User Interface Behaviours*__

In order to extend your application user interface you can add new behaviours to your entities' user interface.

Click [here](omnia3_modeler_uibehaviours.html), to know more about user interface behaviours.

### Accelerators
 
![UI Accelerator](https://raw.githubusercontent.com/OMNIALowCode/omnia3/master/docs/images/modeler/UIaccelerator.png)
 
* **Hide an Element**
The accelerator will allow you to easily select an interface element you wish to hide and add the conditions (value or role) that will trigger that behaviour
Example: A user selects his payment option and that action will hide the unnecessary elements.
 
* **Set Element Read Only**
Easily select an interface element you wish to define as Read Only and add the conditions (value or role) that will trigger that behaviour
Example: Depending on the user role, allow your Supplier to edit the field "Unit Price", while the custumer only sees it as read only. 
 
* **Add Validation Message**
Quickly add validation messages to your interface elements, add the trigger conditions (value or role) and define the content of your message
Example: If a user tries to add an invalid email on a field, an error message is returned indicating that.

### How to hide an element?

In this sample, base element *_code* is set as hidden:

```JavaScript
    this._metadata.elements._code.isHidden = true;
```

### How make an element read-only?

In this sample, base element *_code* is set as read only:

```JavaScript
    this._metadata.elements._code.attributes.isReadOnly = true;
```

### How make an element required in the UI?

In this sample, element *email* is set as required:

```JavaScript
    this._metadata.elements.email.attributes.min = "1";
```

### How to change the size of an element?

In this sample, custom element *supplier* size is changed:

```JavaScript
    this._metadata.elements.supplier.size = 1;
```

### How to set an element value?

In this sample, custom element *supplier* value is changed:

```JavaScript
    this.supplier = "S001";
```

### How to add or remove a message?
In this sample, is removed and added (based on a condition) a message to the base element *_code*:

```JavaScript
    this._metadata.elements._code.removeMessage('validation');
    if(this._code === '')
        this._metadata.elements._code.addMessage('My error message', 'error', 'validation');
    else
        this._metadata.elements._code.addMessage('My success message', 'success', 'validation');
```
*Note*: There are available only two types of message, as shown in the previous sample: **error** and **success**.

### How to manage the state of the add and remove options in an editable list?

In this sample, the options to remove or add records of custom element *collection* are changed based on a condition:

```JavaScript
    // Disable options
    this._metadata.elements.collection.attributes.addEntry = "disabled";
    this._metadata.elements.collection.attributes.removeEntry = "disabled";
    
    // Hide options
    this._metadata.elements.collection.attributes.addEntry = "hidden";
    this._metadata.elements.collection.attributes.removeEntry = "hidden";
        
    // Enable and show options
    this._metadata.elements.collection.attributes.addEntry = "enabled";
    this._metadata.elements.collection.attributes.removeEntry = "enabled";
```


### How to manage the state of the entities default options?

In this sample, the default entity options *Save*, *Show history*, *Delete record* and *Destroy sensitive data* are set as hidden:

```JavaScript
    // Hide History option
    this._metadata.attributes.showHistoryOption = "hidden";
    // or Disable History option
    this._metadata.attributes.showHistoryOption = "disabled";
    
    // Hide Delete option
    this._metadata.attributes.deleteOption = "hidden";
    // or Disable Delete option
    this._metadata.attributes.deleteOption = "disabled";
    
    // Hide Destroy option
    this._metadata.attributes.destroyOption = "hidden";
    // or Disable Destroy option
    this._metadata.attributes.destroyOption = "disabled";
    
    // Hide Save option
    this._metadata.attributes.saveOption = "hidden";
    // or Disable Save option
    this._metadata.attributes.saveOption = "disabled";
```

### How to move an element to the details area of a grid?

This feature only applies to the inner elements of a collection element.
In this sample, the element *notes* (which is an inner element of *collection*) is placed in the details area:

```JavaScript
    this._metadata.elements.collection.elements.notes.attributes.isDetails = true;
```

### How to redirect to another application page?

In this sample, the user will be redirected to another page of the application, using an existing function of the Form/Dashboard *context*:

```JavaScript
    // The application will be redirected to the dashboard of the entity Employee
    this._context.redirectToApplicationAddress('Employee');
```

### How to have asynchronous behaviours?

In this sample, the behaviour returns a [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise), that will allow the behaviour to execute asynchronously:

```JavaScript
    return new Promise(
        (resolve) => {
            // your code here
            resolve();
        }
    );
```

### **Decimal Attributes**
### How to change the number of decimal places of the element?
In this sample, the number of decimal places of the element *decimalField* is setted to a custom value *(3)*. 

```JavaScript
    this._metadata.elements.decimalField.attributes.precision = 3;
```

*Note 1: This is only possible in elements that represent decimal attributes. In the other data types, even this attribute is setted, the value will be ignored.*

*Note 2: This only changes the number of decimal places in the interface. In order to apply decimal places to the server-side data, you need to develop that logic using C# behaviours.*

### **Shared Attributes**
### How to change the shared attribute's lookup list?

In this sample, the lookup list of the attribute *employee* is changed to a custom list:

```JavaScript
    this._metadata.elements.employee.attributes.list = 'MyCustomEmployeeList';
```

### How to filter a shared attribute's lookup list?

In this sample, the lookup list of the attribute *employee* is filtered using the data (in the case, the value of *company*) of the current entity:

```JavaScript
    this._metadata.elements.employee.attributes.listParameters = {
        company: this.company
    };
```

### **Calendar**
### How to set the entries of a calendar?
To each entry is neccessary to define the *date* and the *title*. 
The *category* can also be defined, in order to group the entries.

In this sample, the entries of the element *calendar* are setted:

```JavaScript
    this._metadata.elements.calendar.attributes.entries = [
        { date: '2019-12-25', title: 'Christmas', category: 'Holidays' },
        { date: '2019-12-23', title: 'Vacations: Mary Smith', category: 'EmployeeVacations' },
        ...
    ]
```

### How to set the categories of a calendar?
To each category is possible to define the *name* (used as the unique identifier), a *title* and a *color*. Is also possible to set the category as inactive by default.

In this sample, the categories of the element *calendar* are setted:

```JavaScript
    this._metadata.elements.calendar.attributes.categories = [
        { name: 'Category01', title: 'Le 1st category', color: '#d90dea', startAsInactive: true },
        { name: 'A', title: 'Le "A" category', color: '#259fb4', startAsInactive: false }
    ]
```

### How to change the initial date of a calendar?
In this sample, the date where the calendar will be positioned when is initialized is setted:

```JavaScript
    this._metadata.elements.calendar.attributes.initialDate = '2020-01-06';
```

### How to change the initial view of a calendar?
In this sample, the view in which the calendar is initialized is setted:

```JavaScript
    this._metadata.elements.calendar.attributes.initialView = 'year';
```

The following views are available:

| Value | Description |
| --------- | --------- |
| 'week' | One week view as calendar |
| 'month' | One month view as calendar |
| 'year' | One year view as calendar |
| 'week_schedule' | One week view as schedule |
| 'month_schedule' | One month view as schedule |
| 'year_schedule' | One year view as schedule |


### How to execute an action when the view is changed?

In this sample, a function is added to the calendar metadata, in order to be executed every time the calendar's view is changed:

```JavaScript
    this._metadata.elements.calendar.onDataRangeChange = (startDate, finishDate, view) => {
        // your code here
    }
```

### How to execute an action when a category is toggled?

In this sample, a function is added to the calendar metadata, in order to be executed every time a category is activated or deactivated:

```JavaScript
    this._metadata.elements.calendar.onCategoryToggle = (category, isActive) => {
        // your code here
    }
```

### **Web Components**
The Web Component instance will be available to interact with in the JS object and is identified by the name of the element.

### How to set a value of a Web Component's property?

In this sample, a custom property's value of a Web Component is setted:

```JavaScript
    this.myWebComponent.theProperty = "The new value";
```

### How to call a function of a Web Component?

In this sample, a custom function of a Web Component is executed:

```JavaScript
    this.myWebComponent.theFunction(parameter1, parameterN);
```