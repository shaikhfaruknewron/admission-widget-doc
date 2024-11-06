# Elern Admission Widget

A lightweight, customizable admission form widget that can be easily integrated into any school or educational institution's website.

## Features

- 🎯 Easy Integration
- 🎨 Customizable UI
- 📱 Responsive Design
- ✅ Form Validation
- 📧 Email & Mobile Verification
- 💳 Payment Integration
- 📅 Appointment Scheduling
- 🔄 Real-time Status Updates

## Installation

### Method 1: Direct Script Include

Add the following code to your HTML file:

```html
<head>
    <!-- Add the CSS file -->
    <link rel="stylesheet" href="https://widget.elern.io/dist/elernwidget.css">
    
    <!-- Add the JavaScript file -->
    <script async src="https://widget.elern.io/dist/elernwidget.js"></script>
</head>
```

### Method 2: NPM Installation

```bash
npm install elern-admission-widget
```

## Basic Usage

1. Add a container div where you want the form to appear:

```html
<div id="student-application-form"></div>
```

2. Initialize the widget:

```html
<script>
document.addEventListener('DOMContentLoaded', function() {
    ElernWidget.initializeWidget({
        formId: 'student-application-form',
        templateId: '16'  // Replace with your template ID
    });
});
</script>
```

## Advanced Implementation

### Complete Example with Loading State

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>School Admission Form</title>
    
    <!-- Widget Dependencies -->
    <link rel="stylesheet" href="https://widget.elern.io/dist/elernwidget.css">
    <script async src="https://widget.elern.io/dist/elernwidget.js"></script>
    
    <style>
        /* Loading Spinner */
        .spinner {
            border: 4px solid rgba(0, 0, 0, 0.1);
            width: 36px;
            height: 36px;
            border-radius: 50%;
            border-left-color: #09f;
            animation: spin 1s linear infinite;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Loading State -->
        <div id="loader">
            <div class="spinner"></div>
        </div>
        
        <!-- Form Container -->
        <div id="student-application-form" style="display: none;"></div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const loader = document.getElementById('loader');
            const formContainer = document.getElementById('student-application-form');
            
            // Initialize Widget
            ElernWidget.initializeWidget({
                formId: 'student-application-form',
                templateId: '16',
                submitButton: {
                    text: 'Submit Application',
                    backgroundColor: '#ff0000',
                    textColor: '#ffffff'
                },
                style: {
                    primaryColor: '#ff0000',
                    backgroundColor: '#ffffff',
                    textColor: '#000000',
                    borderRadius: '4',
                    fontSize: '14',
                    fontFamily: 'Arial'
                }
            });

            // Check for form rendering
            const checkFormRendered = setInterval(function() {
                if (formContainer.children.length > 0) {
                    clearInterval(checkFormRendered);
                    loader.style.display = 'none';
                    formContainer.style.display = 'block';
                }
            }, 100);

            // Fallback loader hide
            setTimeout(function() {
                clearInterval(checkFormRendered);
                loader.style.display = 'none';
                formContainer.style.display = 'block';
            }, 5000);
        });
    </script>
</body>
</html>
```

## Configuration Options

### Basic Configuration

```javascript
{
    formId: 'student-application-form',  // ID of container element
    templateId: '16',                    // Your template ID
    apiEndpoint: 'https://api.example.com/admission', // Optional custom API endpoint
}
```

### Style Customization

```javascript
{
    style: {
        layout: 'inline',              // 'inline' or 'stacked'
        primaryColor: '#ff0000',       // Primary brand color
        backgroundColor: '#ffffff',     // Form background color
        textColor: '#000000',          // Text color
        borderRadius: '4',             // Border radius for elements
        fontSize: '14',                // Base font size
        fontFamily: 'Arial',           // Font family
        previewSize: 'large',          // Size of preview elements
        gap: '0.5rem',                 // Spacing between elements
    }
}
```

### Submit Button Customization

```javascript
{
    submitButton: {
        text: 'Apply Now',             // Button text
        backgroundColor: '#ff0000',     // Button background color
        textColor: '#ffffff',          // Button text color
        borderRadius: '4'              // Button border radius
    }
}
```

## Form Fields Configuration

The widget supports various field types:

```javascript
{
    fields: [
        {
            id: 1,
            type: 'text',              // Field type
            label: "Student's Name",    // Field label
            required: true,             // Is field required?
            field: 'name',             // Field identifier
            width: 'full',             // Field width ('full', 'half')
            order: 1                   // Display order
        },
        // More fields...
    ]
}
```

Supported field types:
- `text`
- `email`
- `tel`
- `select`
- `date`
- `file`

## Verification Features

### Email Verification

```javascript
{
    setup: {
        emailVerification: true,
        emailOptions: {
            beforeSubmission: true,    // Verify before form submission
            afterSubmission: false     // Verify after form submission
        }
    }
}
```

### Mobile Verification

```javascript
{
    setup: {
        mobileVerification: true,
        mobileOptions: {
            mobilebeforeSubmission: true,
            mobileafterSubmission: false
        }
    }
}
```

## Payment Integration

The widget supports payment integration with Razorpay. Configure payment options:

```javascript
{
    payment: {
        gateway: 'razorpay',
        currency: 'INR',
        theme: {
            color: '#ff0000'
        }
    }
}
```

## Events and Callbacks

Listen to widget events:

```javascript
document.addEventListener('widgetLoaded', function(e) {
    console.log('Widget loaded successfully');
});

document.addEventListener('formSubmitted', function(e) {
    console.log('Form submitted:', e.detail);
});

document.addEventListener('paymentComplete', function(e) {
    console.log('Payment completed:', e.detail);
});
```

## Troubleshooting

Common issues and solutions:

1. Widget not loading
   - Check if all dependencies are properly loaded
   - Verify your template ID
   - Check console for errors

2. Style not applying
   - Ensure CSS file is properly linked
   - Check if style configuration is correctly formatted
   - Verify CSS class names

3. Payment integration issues
   - Confirm Razorpay configuration
   - Check API keys
   - Verify payment callback URLs

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Opera (latest)

## Contributing

We welcome contributions! Please see our contributing guidelines for more details.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

For support, please email support@elern.io or visit our documentation at https://docs.elern.io
