# CodeSnippets

Some code snippets for Visual Studio.

## AvaloniaUI

* avaap

    ```csharp
    
        public static readonly AttachedProperty<object> MyPropertyProperty =
            AvaloniaProperty.RegisterAttached<MyClass, Control, object>("MyProperty");

        public static object GetMyProperty(Control element) => element.GetValue(MyPropertyProperty);

        public static void SetMyProperty(Control element, object value) => element.SetValue(MyPropertyProperty, value);

    ```

* avadp

    ```csharp
        public static readonly DirectProperty<MyControl, object> MyPropertyProperty =
            AvaloniaProperty.RegisterDirect<MyControl, object>(
                nameof(MyProperty),
                o => o.MyProperty,
                (o, v) => o.MyProperty = v);

        private object _field = new object();

        public object MyProperty
        {
            get => _field;
            set => SetAndRaise(MyPropertyProperty, ref _field, value);
        }
    ```
* avadpao

    ```csharp
        public static readonly DirectProperty<MyControl, object> MyPropertyProperty =
            AvaloniaProperty.RegisterDirect<MyControl, object>(
                nameof(MyProperty),
                o => o.MyProperty);

        private object _field;

        public object MyProperty
        {
            get => _field;
            private set => SetAndRaise(MyPropertyProperty, ref _field, value);
        }
    ```
* avarp

    ```csharp
        public static readonly DirectProperty<MyControl, object> MyPropertyProperty =
            AvaloniaProperty.RegisterDirect<MyControl, object>(
                nameof(MyProperty),
                o => o.MyProperty);

        private object _field;

        public object MyProperty
        {
            get => _field;
            private set => SetAndRaise(MyPropertyProperty, ref _field, value);
        }
    ```
* avasp

    ```csharp
    
        public static readonly StyledProperty<object> MyPropertyProperty =
            AvaloniaProperty.Register<MyControl, object>(nameof(MyProperty));

        public object MyProperty
        {
            get => GetValue(MyPropertyProperty);
            set => SetValue(MyPropertyProperty, value);
        }


    ```
* avaspao

    ```csharp
        public static readonly StyledProperty<IBrush> BackgroundProperty =
            Border.BackgroundProperty.AddOwner<MyControl>();

        public object Background
        {
            get => GetValue(BackgroundProperty);
            set => SetValue(BackgroundProperty, value);
        }
    ```