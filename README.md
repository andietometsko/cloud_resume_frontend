# Frontend

The frontend of this project is a static website that showcases the resume and is hosted on AWS S3 with secure, high-speed content delivery through CloudFront.

## Frontend Components

### HTML
The resume content is coded in HTML, including sections such as the profile, experience, skills, and education.

- **Requirements**: The HTML file should be clean, well-structured, and contain only necessary information (avoid personal email or phone numbers for security).
- **Best Practices**: Semantic HTML tags are recommended for accessibility and SEO.

### CSS
CSS is used to style the resume and ensure it is visually appealing and responsive across devices.

- **Structure**: Organized using a separate CSS file (`style.css`), which includes styling for fonts, layout, colors, and spacing.
- **Template**: You may use a free or custom CSS template as a base for the design, but it should reflect a professional look suitable for a portfolio.

### JavaScript
The main interactive feature of the frontend is the visitor counter that displays the number of site visits.

- **Visitor Counter Logic**: JavaScript fetches the visitor count from the backend API and displays it on the page.
- **Fetch Request**: The JavaScript file (`visitor-counter.js`) makes an asynchronous fetch call to the API endpoint, retrieves the count, and updates the HTML element displaying the counter.
- **Error Handling**: Basic error handling ensures that if the API call fails, the user receives a friendly message, and the counter defaults to zero or a placeholder message.

## Hosting & Security

### S3 Static Website Hosting
- The website files (HTML, CSS, JS) are stored in an S3 bucket configured for static website hosting.
- **Configuration**: The S3 bucket is set with the required bucket policy to allow public access, enabling the website to be accessible over the web.

### CloudFront & HTTPS
- To secure the connection, an SSL certificate from AWS Certificate Manager (ACM) is used in combination with a CloudFront distribution.
- **CloudFront**: Configured to serve the website through HTTPS, delivering content securely and quickly with caching benefits.
- **Domain & DNS**: The custom domain is managed through Route 53, ensuring visitors can access the website through an easy-to-remember URL.

## CI/CD for Frontend

### GitHub Actions Workflow
The CI/CD pipeline automates deployment to S3.

- **Deployment Trigger**: When changes are pushed to the GitHub frontend repository, the workflow automatically uploads new files to the S3 bucket.
- **Cache Invalidation**: After deployment, the workflow invalidates the CloudFront cache, ensuring the updated site is immediately available to visitors.
