# UML-API: UML to Code Generation API

Transform UML diagrams into executable code with ease. 🚀

## 📝Overview

UML-API is a powerful and extensible API that converts UML diagram specifications into executable code. Developed by Latrina Maxima, this project is built with TypeScript, Express, and Handlebars, providing a flexible framework for generating code from UML models.

Whether you're a developer prototyping software designs or an educator teaching object-oriented programming, UML-API streamlines the process of turning UML representations into functional code.

## ✨ Features

- UML to Code Generation: Convert UML specifications into code
- Validation: Robust input validation 
- Type Safety: Leverages TypeScript with custom types for compile-time safety
- Extensible Templates: Powered by Handlebars for easy customization of code output
- RESTful API: Simple and intuitive code generation endpoint
- Developer-Friendly: Auto-restart with nodemon during development, ES Modules for modern JavaScript

## 🧰Tech Stack

- TypeScript
- Express
- Ajv
- Handlebars
- Node.js
- ts-node & nodemon

## 📋Prerequisites

- Node.js (v18 or higher)
- npm (v8 or higher)

## 🔧Installation

1. Clone the Repository:
```bash
git clone https://github.com/latrina-maxima/uml-api.git
```

2. Install Dependencies:
```bash
npm install
```

3. Build the Project:
```bash
npm run build
```

## 🚀Running the API

### Development Mode
```bash
npm run dev
```
This starts the server with auto-restart enabled.

### Production Mode
```bash
npm start
```

## 📂Project Structure
```
uml-api/
├── dist/
├── node_modules/
├── src/
│   ├── generation/
│   │   ├── templates/
│   │   │   └── javaClass.hbs
│   │   └── generator.ts
│   ├── validation/
│   │   └── validator.ts
│   └── index.ts
├── .env
├── .gitignore
├── LICENSE
├── package-lock.json
├── package.json
├── README.md
├── CONVENTIONS.md
└── tsconfig.json
```

## 📝 Coding Conventions

This project follows strict TypeScript coding conventions to ensure code quality and maintainability. Our conventions cover:

- Strong typing practices
- Variable and function declarations
- Naming standards
- Code structure guidelines
- Import organization

All contributors should review the complete [CONVENTIONS.md](./CONTRIBUTING.md) file before submitting code. These conventions help us maintain consistency across the codebase and improve collaboration among team members.

## 🤝Contributing

We welcome contributions! To get started:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/your-feature`)
3. Make your changes and commit (`git commit -m "feat: add your feature"`)
4. Ensure your code follows our [coding conventions](./CONTRIBUTING.md)
5. Push to your branch (`git push origin feature/your-feature`)
6. Open a Pull Request

Please follow the Conventional Commits specification for commit messages.

## 🔮Future Plans

- Expand language support
- Enhance code generation capabilities
- Cloud platform deployment

## 👥Contributors

- Mark Ulanovskyi
- Kirill Shubenok

## 📄License

This project is licensed under the MIT License.

## 📞Contact

- Organization: Latrina Maxima
- GitHub: [Latrina Maxima](https://github.com/Latrina-Maxima)
- Email: maximalatrina@gmail.com

Built with ❤️ by Latrina Maxima.