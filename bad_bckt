# main.tf
# This terraform file defines our primary S3 bucket.

provider "aws" {
  region = "us-east-1"
}

# DANGER: This S3 bucket is publicly accessible.
# An IaC scanner will identify the "public-read" ACL
# as a critical security misconfiguration.
resource "aws_s3_bucket" "company_data" {
  bucket = "my-company-sensitive-data-12345"
  
  # This line creates the security vulnerability
  acl = "public-read"

  tags = {
    Name        = "Company Data"
    Environment = "Prod"
  }
}

# A more secure configuration would look like this:
/*
resource "aws_s3_bucket" "secure_bucket" {
  bucket = "my-company-secure-data-67890"
  acl    = "private" # This is the default and is secure.
}

resource "aws_s3_bucket_public_access_block" "secure_bucket_block" {
  bucket = aws_s3_bucket.secure_bucket.id

  block_public_acls       = true
  block_public_policy     = true
  ignore_public_acls      = true
  restrict_public_buckets = true
}
*/
