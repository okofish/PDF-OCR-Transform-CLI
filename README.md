# PDF-OCR-Transform-CLI
CLI tool for transforming third party OCR formats into Labelbox's proprietary pdf text layer format. The CLI takes a folder containing pdfs as input, runs an OCR algorithm on the pdfs, and produces Labelbox text layer json files as an output.

Currently Supported OCR formats:
* Textract
* Adobe (coming soon)
* GCP (coming soon)

# Prerequisites
The CLI invokes the `aws` cli behind the scenes to upload the pdfs to s3 and invoke Textract on them. You must have the aws cli installed gloablly and configured for your aws user.

[Install AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

[Configuring the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-prereqs.html)

# Configuration
There is a configuration file named `config.json` at the root level of the directory that must be updated before first running the CLI.
```
{
  // PDFS will be uploaded to s3://<s3Bucket>
  "s3Bucket": "<name_of_s3_bucket>"
}
```


# Usage
Included are bundled executables for multiple platfoms `text-layermacos`, `textlayer-linux`, `textlayer-win.exe`. These provide a more portable version of the cli that don't require you to install all the necessary dependencies with `npm install`.

## Commands:

Run OCR on all pdfs contained in the input folder and convert the result into Labelbox's text layer JSON.

`convert --inputFolder <input_folder_containing_pdfs> --format <textract> --outputFolder <output_folder>`

Example (Mac)
```
./textlayer-macos convert --inputFolder input --format textract --outputFolder output
```

Help page
```
./textLayer convert --help
```

# (Optional) Build Scripts
You only need to build the cli if you wish to run the source code locally as opposed to using the provided executables.

Install Dependencies
```
npm install
```

Build the CLI
```
npm run build
```

Development - Build the CLI with hot reloading
```
npm run start
```

The CLI has been bundled with [pkg](https://www.npmjs.com/package/pkg).
