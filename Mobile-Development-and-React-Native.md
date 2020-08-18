# Mobile Development and React Native

## Forms

Forms are one of the most annoying parts for users, so the more we can turn the experience of filling them out into something good, the less discomfort will be caused. Therefore, some react-native resources used for these purposes will be highlighted.


### Focus on the next input and submit directly from the keyboard

It is very annoying when we are filling out a form on the cell phone and we need to scroll down and select the next input. For this reason, mobile keyboards have a return key to assist in this case. The return key is usually found at the lower right corner of the keyboards and we can pass a function to be executed when it's pressed, such as to focus on the next text field or submit the form. Some platforms even allow you to replace it's label for best suit your use case.

The two attributes for React native's TextInput component that will help you with this are returnKeyType and onSubmitEditing.

**returnKeyType**

Defines a label for the return button, that is, it places the ideal name for the button in the lower corner, mentioned above.
The default values ​​can be:
- `done`
- `go`
- `next`
- `search`
- `send`

*How to use:*

    <TextInput
	    id="name"
	    value={name}
	    onChange={handleOnChange}
	    returnKeyType="next"
    />

*Result:*

Used in text fields to point to the next:

![Used in text fields to point to the next](./assets/mobile-development/button-next.png)


**onSubmitEditing**

Now that you know how to make the return buttons have coherent names, it is necessary to know how to add the functions that will make life easier for users. For this, onSubmitEditing is used, in which you can assign a function to focus on the next text field or submit the form. See the examples:

*How to use:*

    const inputRefLastName = useRef(null)
    
    <TextInput
      id="firstName"
      value={firstName}
      onChange={handleOnChange}
      returnKeyType="next"
      onSubmitEditing={() => inputRefLastName.current.focus()}
    />
    <TextInput
      id="lastName"
      ref={inputRefLastName}
    value={name}
      onChange={closeKeyboard}
      returnKeyType="done"
      onSubmitEditing={closeKeyboard}
    />

*Result:*

![Used onSubmitEditing](./assets/mobile-development/on-submit-editing.gif)

### Keyboard Types

The `keyboardType` attribute defines which type of keyboard to open when the user taps a text field. This way you make it easier for the user when the field is to fill the phone by adding the `phone-pad` type, for example.

![phone pad keyboard](./assets/mobile-development/phone-pad.png)

The standard values that can be used are ([See the react-native documentation for others](https://reactnative.dev/docs/textinput#keyboardtype)):

-   `default`
-   `number-pad`
-   `decimal-pad`
-   `numeric`
-   `email-address`
-   `phone-pad`


### autoCapitalize

The `autoCapitalize` attribute is used to tell the keyboard to capitalize certain characters. In this way, we can make it easier for the user to type in their full name by adding the type `words` that leave the initial letter of each word in more capital.
The values that can be used are:

-   `characters`: all characters
-   `words`: first letter of each word
-   `sentences`: first letter of each sentence (default)
-   `none`: do not capitalize automatically





*@CONTRIBUTE Please teach me the ways of RN, master...*
