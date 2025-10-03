# Customer Account Pages

This document describes the customer registration and login pages that have been added to the theme.

## Overview

Two new customer account pages have been created:
- **Registration Page** (`/account/register`) - Allows new customers to create an account
- **Login Page** (`/account/login`) - Allows existing customers to sign in

## Features

### Design
- Clean, centered layout with optional logo
- Icon-decorated form fields (user, email, lock icons)
- Green primary action button
- Consistent styling across both pages
- Responsive design for all screen sizes
- Form validation and error display

### Customization Options

#### Logo
Both pages support an optional logo that can be configured in the theme editor:
1. Go to the theme editor
2. Navigate to the register or login page
3. Select the section
4. Upload a logo image in the section settings

The logo will be displayed as a circular image (120x120px) at the top of the form.

#### Text Customization
All text on these pages can be customized via the locale files:
- `locales/en.default.json` - Contains all customer-facing text
- Edit the `customers.register` and `customers.login` keys to change text

Example locale keys:
```json
{
  "customers": {
    "register": {
      "title": "Create Account",
      "subtitle": "Join the Board Game community",
      "full_name": "Full Name",
      "email": "Email Address",
      "password": "Password",
      "submit": "Create Account"
    }
  }
}
```

## How to Enable

1. **Enable Customer Accounts in Shopify Admin:**
   - Go to Settings > Checkout
   - Under "Customer accounts", select "Accounts are optional" or "Accounts are required"

2. **Test the Pages:**
   - Visit `https://your-store.myshopify.com/account/register` for registration
   - Visit `https://your-store.myshopify.com/account/login` for login

## Navigation

The pages are linked to each other:
- Registration page has a "Already have an account? Sign in" link
- Login page has a "New customer? Create account" link

These links use Shopify's built-in routes:
- `{{ routes.account_login_url }}` - Link to login page
- `{{ routes.account_register_url }}` - Link to registration page

## Form Fields

### Registration Page
- **Full Name** (required) - Uses `customer[first_name]` field
- **Email Address** (required) - Uses `customer[email]` field
- **Password** (required) - Uses `customer[password]` field

### Login Page
- **Email** (required) - Uses `customer[email]` field
- **Password** (required) - Uses `customer[password]` field

## Styling

The pages use inline CSS via the `{% stylesheet %}` tag, following the theme's conventions:
- CSS variables from `snippets/css-variables.liquid` for colors
- Consistent border-radius and spacing
- Focus states for accessibility
- Hover effects on buttons and links

## Icons

Three SVG icons are used across the pages:
- `icon-account.svg` - User/person icon (existing)
- `icon-email.svg` - Email/envelope icon (new)
- `icon-lock.svg` - Lock/security icon (new)

All icons are inlined using the `inline_asset_content` filter for better performance.

## Error Handling

Both forms use Shopify's built-in error handling:
- `{{ form.errors | default_errors }}` displays validation errors
- Errors are styled with a red background and border
- Error messages are displayed above the form

## Browser Support

The pages use modern CSS features but maintain broad browser support:
- Flexbox for layout
- CSS variables (with fallbacks via Liquid)
- Standard HTML5 input types
- Progressive enhancement approach

## Accessibility

- Proper label/input associations
- Semantic HTML structure
- Focus states on interactive elements
- Appropriate input types (email, password, text)
- Autocomplete attributes for better UX

## Future Enhancements

Potential improvements that could be added:
- Password strength indicator
- Show/hide password toggle
- Social login options
- Remember me checkbox
- Forgot password link
- Email verification messaging
