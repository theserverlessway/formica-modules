# CloudFront Web Bucket

This modules deploys two Buckets backed by two CloudFront distributions for your static websites. You can either provide an ACM certificate, or one will be created for you automatically to support https. The second Bucket and distribution are to redirect www to the main website.

It also sets up DNS CNames automatically for your stack.

The buckets are public by default to make it possible to use the built-in webserver like behaviour of S3 (mostly to support index files in any subfolder). This setup is therefore not intended for use where files should be hidden or not accessible in the bucket.