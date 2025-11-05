# silver-sniffle
Demo of authenticating access to files.

## How to run the walkthrough
- Open `file_access_demo.ipynb` in Jupyter (VS Code, JupyterLab, or `jupyter notebook`).
- Execute the cells sequentially. Each section introduces one layer of the stack (mock S3, auth provider, GraphQL API, download service, and a plain HTML client).
- Observe how the naïve flow forces an S3 bucket to be public and how the secure flow keeps the bucket private by proxying downloads through an authenticated service.

## Key ideas reinforced in the notebook
- Never hand raw S3 URLs back to the browser unless the object is meant to be public.
- Reuse your existing authentication provider so both GraphQL and the download service trust the same bearer token.
- Issue short-lived, single-use download tokens that the download service can verify before streaming the file from S3.
