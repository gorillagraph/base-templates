# Rave Base Assets

This repository serves as a starting point for customizing HTML templates and static files tailored to customer branding. Follow the steps below to get started.

## Usage

1. Fork this repository to your own GitHub account.

> [!WARNING]
> It's important to ensure that the repository is protected from unauthorized changes. This may involve setting up branch protection rules, access permissions, or enabling required reviews for pull requests. By doing so, you can ensure that only authorized individuals can make changes to the repository and maintain control over the deployment process. Reach out to the Rave Support Team if you need help configuring the appropriate repository settings.

2. Clone the forked repository to your local development environment.

    ```shell
    git clone https://github.com/<your-account>/<your-fork-name>.git
    ```

3. Make the necessary changes to the HTML templates or static files.

4. Generate an Auth Token in the **Settings > Templates** section of the Rave Developer Portal.

5. Configure the generated authorization token as a variable in the repository settings, this is required for the deployment workflow action to automatically publish changes whenever a commit is pushed to a release branch.

    - `AUTH_TOKEN`: The Auth Token obtained from the Rave Developer Portal.


> [!TIP]
> Please make sure to [use environments for deployments](https://docs.github.com/en/actions/deployment/targeting-different-environments/using-environments-for-deployment), this will allow using the same repository to deploy across different environments, see [Creating an environment](https://docs.github.com/en/actions/deployment/targeting-different-environments/using-environments-for-deployment#creating-an-environment) for instructions on how to set up one.
>
> It's also recommended to configure a [deployment branch](https://docs.github.com/en/actions/deployment/targeting-different-environments/using-environments-for-deployment#deployment-branches) for the environment, to restrict the branch that is allowed to deploy to the underlying environment. For example, in a `develop` environment, limit it to the `release-develop` branch, this will ensure that only this branch will be able to trigger a deployment to the `develop` environment.


6. Publish Changes:

    - Enable GitHub actions on your project. You can do this by navigating to the "Actions" tab and ensuring that workflows are enabled. Note that workflows are initially disabled by default on forks.
    - Enable GitHub issues feature on your project. You can do this by navigating to the project settings and ensuring issues is enabled under features. This will be required to notify if a deployment requires manual review.
    - For changes to be automatically published, a commit needs to be pushed to a branch with a prefix of `release-` following the branch naming convention: `release-environment-name`. For example: `release-develop`. This will ensure that the variables are pulled from correct environment, allowing multi environment deployments.
    - Push your changes to the appropriate release branch.
    - Manual Action Required for Deployment:

> [!IMPORTANT]
> If the deployment pipeline identifies files that require manual review, it will pause and create an issue for attention. The author of the deployment must then review the issue and decide how to proceed with the deployment.
>
> This approval process is subject to the broader 72-hour timeout for a workflow. Keep this duration in mind to ensure timely responses from approvers. Delays in approval may necessitate re-initiation of the deployment process.

7. Deployment:

    - Your application should be configured to fetch the latest templates from the repository based on the specific environment branch. Ensure that your deployment process includes pulling the latest changes from the desired release branch.

## Assets Structure

The repository is structured as follows:

- 📂 **templates**: This folder contains web page layouts, such as the reset password page. You can modify the HTML files in this folder to customize the visual appearance and base structure of your web pages.

- 📂 **templates/email**: This folder contains templates specifically designed for sending emails. Each email template consists of an HTML file and a corresponding plain text (TXT) file. The HTML file represents the actual email content, while the plain text file serves as the email body for clients that do not support HTML rendering. Please refer to the documentation in each HTML file for information on what is available on each template.

- 📂 **templates/static/images**: This folder contains static images that are used across the HTML templates. Any image files you want to include in your templates should be placed in this folder. You can reference these images in your HTML templates to display logos, icons, or other visual elements.


## Contributing

If you find any issues or have suggestions for improvements, feel free to open an issue or submit a pull request. We appreciate your contributions!

## License

This repository is licensed under the [MIT License](LICENSE).
