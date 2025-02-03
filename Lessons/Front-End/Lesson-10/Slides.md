---
marp: true

---
# Web Development

## Front-End Development


---

## Today's Topics

- Review of the previous lecture
- [Pagination](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Frameworks/Topics/React-Pagination/README.md)
- [Deploying a React Application](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Frameworks/Topics/Deploy/README.md)
- Topics Not Covered in the Course
- Course Summary and Feedback
- What's Next?

---

## What Did We Discuss Last Time?

---

## Pagination

Pagination is a common method for dividing large datasets into smaller, manageable parts, improving page load time and enhancing user experience.

It also reduces server and network load by loading data incrementally.

---

## How Does Pagination Work?

Essentially, pagination allows us to request data from an API in pages. For example, instead of loading all 1000 users at once, we can load 10 users per page. Common parameters for this include `page` and `limit`, such as `/users?page=1&limit=10`.

> Remember, pagination support and implementation can vary across APIs.

---

## React Bootstrap Pagination Component

React Bootstrap provides a `Pagination` component, enabling us to create an elegant pagination UI component that we can use across our application.

---

## Example: Pagination in React with React Bootstrap

We’ll add a `PaginationComponent` to display data page-by-page.

---

## PaginationComponent

```javascript
import React from 'react';
import { Pagination } from 'react-bootstrap';

const PaginationComponent = ({ currentPage, totalPages, onPageChange }) => {
  const pageNumbers = [];

  for (let i = 1; i <= totalPages; i++) {
    pageNumbers.push(i);
  }

  return (
    <Pagination>
      <Pagination.First onClick={() => onPageChange(1)} disabled={currentPage === 1} />
      <Pagination.Prev onClick={() => onPageChange(currentPage - 1)} disabled={currentPage === 1} />
      {pageNumbers.map(number => (
        <Pagination.Item key={number} active={number === currentPage} onClick={() => onPageChange(number)}>
          {number}
        </Pagination.Item>
      ))}
      <Pagination.Next onClick={() => onPageChange(currentPage + 1)} disabled={currentPage === totalPages} />
      <Pagination.Last onClick={() => onPageChange(totalPages)} disabled={currentPage === totalPages} />
    </Pagination>
  );
};

export default PaginationComponent;
```

---

## Using PaginationComponent

To use `PaginationComponent`, we need to handle a few things:

- The API must support paginated data requests.
- Track the current active page.
- Know the total pages (and items per page).
- Trigger a new API call when the page changes.
- Update application state when API data is returned.

---

## Implementing PaginationComponent - Component Setup

```javascript
import PaginationComponent from './PaginationComponent';
...
{posts && <PaginationComponent
  totalPages={pagination.totalPages}
  currentPage={currentPage}
  onPageChange={(pageNumber) => setCurrentPage(pageNumber)}
/>
}
...
```

- Display  `PaginationComponent`only if data is present.
- Pass required parameters to `PaginationComponent`
- Update the application state when the user changes the page.

---

## Making the API Request

```js
...
const [pagination, setPagination] = useState(null); // pagination data
const [currentPage, setCurrentPage] = useState(1); // current page
const limit = 10; // items per page
...
const token = localStorage.getItem('token');
const response = await axios.get(`https://blog.hk.tlu.ee/posts?page=${currentPage}&limit=${limit}`, {
  headers: {
    Authorization: `Bearer ${token}`,
  },
});
setPosts(response.data.posts);
setPagination(response.data.pagination);


```

- Pass page number and page size as query parameters.
- Update `posts` and `pagination` state with the API response.

---

## Updating the List on Page Change

```js
useEffect(() => {
  fetchPosts();
}, [currentPage]);

```

- Use the `useEffect` hook to fetch data when the component loads.
- Re-run `fetchPosts` whenever `currentPage` changes.

---

## Deploying a React Application

After completing your React application, you’ll likely want to make it publicly available. Today, we’ll cover deploying a React app to GitHub Pages.


---

## Deployment Preparation

- Create a repository for your project
- Upload/copy your React application to the repository

---

## Deployment Steps

- Install the `gh-pages` package
  - `npm install gh-pages`

---

## Configuring package.json

Add the following lines to `package.json`:

This line sets the homepage URL:

```json
"homepage": "https://<GitHub-username>.github.io/<repository-name>",
```

in `scripts`, add:

```json
  "predeploy": "npm run build",
  "deploy": "gh-pages -d build"
```

---

## Running the Deployment Workflow

```bash
npm run deploy
```

---

## Configuring GitHub Pages

- In your project’s GitHub settings:
  - Go to Settings
  - Go to Pages
    - Source: `Deploy from branch`
    - Branch: `gh-pages` `/root`
  - Your app should be available at:  `https://<GitHub-username>.github.io/<repository-name>`

---

## Next Steps

If everything is configured correctly, your React app should be successfully deployed to GitHub Pages.

For future updates:

- Make changes in your code.
- Run `npm run deploy` to re-deploy.

---

## React Router and GitHub Pages

If you’re using React Router, note that GitHub Pages may not support it as expected. To make it work, replace `BrowserRouter` with `HashRouter`.

```javascript
import { HashRouter as Router } from 'react-router-dom';
```

This change ensures that React Router works correctly with GitHub Pages.

---

## Topics Not Covered in the Course

- Front-End Application Testing
- React Server-Side Rendering (SSR)
- Documentation (we touched on this but didn’t cover it in depth)
- File Uploads (e.g., images, documents)
- File Optimization (images, scripts, styles)
- SEO (Search Engine Optimization)
- Multi-Language Support
- ...

---

## Course Summary and Feedback

- What went well?
- What could be improved?
- Any topics you’d like to explore further?
- Additional thoughts?

---
