# Multistep Form

A multistep form built with Vue.js, TypeScript, and Vite, designed to guide users through a step-by-step process. This project includes configuration for TypeScript, Vite, and Tailwind CSS for styling.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Form Configuration](#form-configuration)
- [Project Structure](#project-structure)

## Features

- **Multistep Form Navigation**: Seamlessly navigate through multiple form steps.
- **Vue 3 Composition API**: Written using Vue 3's Composition API for a modular and modern structure.
- **TypeScript**: Strong typing support with TypeScript.
- **Tailwind CSS**: Utility-first CSS framework for fast and responsive design.
- **Vite**: Lightning-fast development with Vite.

## Installation

### Prerequisites

- Node.js (version 16 or higher recommended)
- npm or yarn

### Steps

1. Clone the repository:

   ```bash
   git clone https://github.com/kevinjeonghun/multistep-form.git
   cd multistep-form
   ```

2. Install dependencies:

   ```bash
   npm install
   ```

3. Start the development server:

   ```bash
   npm run dev
   ```

4. Open the project in your browser:

   ```
   http://localhost:3000
   ```

## Usage

- **Building for Production**:

  To build the project for production, run:

  ```bash
  npm run build
  ```

  The production build will be output to the `dist` folder.

- **Testing the Production Build**:

  To preview the production build locally:

  ```bash
  npm run preview
  ```

## Configuration

### TypeScript

This project uses TypeScript for type-checking. Type definitions for Vue files are configured in `src/shims-vue.d.ts`.

### Tailwind CSS

Tailwind CSS is used for styling. You can modify the configuration in `tailwind.config.js` as needed.

### Vite

The project is bundled with Vite. Configuration options can be found in `vite.config.ts`.

## Form Configuration

The form steps and fields are defined in the following JSON structure:

```json
[
  {
    "step": 1,
    "title": "Personal Information",
    "description": "Please fill out your personal information",
    "fields": [
      {
        "type": "textfield",
        "label": "Name",
        "placeholder": "Enter your name",
        "required": true
      },
      {
        "type": "radio",
        "label": "Gender",
        "options": [
          {
            "label": "Male",
            "value": "male"
          },
          {
            "label": "Female",
            "value": "female"
          },
          {
            "label": "Other",
            "value": "other"
          }
        ],
        "required": true
      }
    ]
  },
  {
    "step": 2,
    "title": "Additional Information",
    "description": "Please provide additional details",
    "fields": [
      {
        "type": "textarea",
        "label": "Description",
        "placeholder": "Enter a description",
        "required": false
      },
      {
        "type": "autocomplete",
        "label": "Title",
        "placeholder": "Enter a title",
        "options": ["Mr.", "Mrs.", "Ms.", "Dr.", "Prof."],
        "required": true
      }
    ]
  }
]
```

## Project Structure

```plaintext
├── public               # Static assets
├── src
│   ├── assets           # Asset files
│   ├── components       # Vue components
│   ├── App.vue          # Root Vue component
│   ├── main.ts          # Entry file
│   └── shims-vue.d.ts   # TypeScript shim for Vue files
├── index.html           # HTML template
└── vite.config.ts       # Vite configuration
```

![Status](https://img.shields.io/badge/Status-Rejected-blue)
