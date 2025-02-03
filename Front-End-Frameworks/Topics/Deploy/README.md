# Deploying a React Project to GitHub Pages

Deploying a React application means hosting it on a server or hosting service so it can be publicly accessed. In this guide, we will explore how to deploy a React project using various methods, including GitHub Pages.

![React Deploy](React-Deploy.webp)

Image Source: Dall-E by OpenAI

- [Deploying a React Project to GitHub Pages](#deploying-a-react-project-to-github-pages)
  - [Learning Outcomes](#learning-outcomes)
  - [Steps for Deploying a React Project](#steps-for-deploying-a-react-project)
  - [Deploying to GitHub Pages](#deploying-to-github-pages)
  - [Prerequisites](#prerequisites)
  - [Steps](#steps)
  - [React Router and GitHub Pages](#react-router-and-github-pages)
  - [Alternative Hosting Platforms](#alternative-hosting-platforms)
  - [Review Questions](#review-questions)
  - [Exercise](#exercise)
  - [Resources](#resources)

## Learning Outcomes

After completing this chapter, you should be able to:

- Explain different methods for deploying a React application.
- Deploy a React application using GitHub Pages.
- Use alternative hosting platforms such as Vercel and Netlify.

---

## Steps for Deploying a React Project

Deploying a React application typically involves the following steps:

- Creating a project repository
- Writing the code
- Installing the `gh-pages` module
- Configuring the `package.json` file
- Running the `deploy` script
- Setting up GitHub Pages
- Verifying the application

---

## Deploying to GitHub Pages

GitHub Pages is a simple way to host static websites, including React applications, as it is free and easy to use. Here is a step-by-step guide to deploying your React application to GitHub Pages.

---

## Prerequisites

- **GitHub Account**: Ensure you have a GitHub account and your project is uploaded there.

---

## Steps

1. Create a repository for your project.
2. Copy or create your React application in the repository.
3. Install the `gh-pages` module:
   - `npm install gh-pages`
   - Add the following line to your package.json file `"homepage": "https://<Githubi kasutajanimi>.github.io/<repositooriumi nimi>",`
4. Add the following scripts to the scripts section in package.json
```bash
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build"
```
5. Run the deployment script `npm run deploy`
6. Configure GitHub Pages:
 -  Go to your repository's Settings.
 -  Navigate to Pages:
    - Source: Select Deploy from branch.
    - Branch: Select gh-pages /root.
 - Access your application at `https://<Githubi kasutajanimi>.github.io/<repositooriumi nimi>`

If everything is set up correctly, your React application should be successfully deployed on GitHub Pages.

## React Router and GitHub Pages

If your application uses React Router, GitHub Pages might not work as expected. To ensure proper functioning, replace BrowserRouter with HashRouter in your application.

```javascript
import { HashRouter as Router } from 'react-router-dom';
```

This change ensures that React Router works properly with GitHub Pages.

## Alternative Hosting Platforms

In addition to GitHub Pages, several other platforms provide simple and efficient ways to host React applications, such as:

- **Vercel**: A popular serverless hosting service for React applications with no configuration needed.
- **Netlify**: Another popular hosting service offering automatic deployment, HTTPS, and more.
- **Heroku**: A platform for deploying and hosting various applications, including React applications.
- Other hosting services that support React applications or static websites.

## Review Questions

1. What are the main steps for deploying a React project?
2. How do you configure a React project for deployment to GitHub Pages?
3. What alternative platforms are available for hosting React applications?

## Exercise

- **Deploy a React application to GitHub Pages**: Use this guide to create and deploy your React application on GitHub Pages.
- **Try Vercel or Netlify**: Create an account on Vercel or Netlify and deploy your React application.

## Allikad

- [Deploying a React App to GitHub Pages](https://create-react-app.dev/docs/deployment/#github-pages)
- [GitHub Pages Documentation](https://pages.github.com/)
- [Vercel Documentation](https://vercel.com/docs)
- [Netlify Documentation](https://docs.netlify.com/)
