# Crypteron CipherTool

Crypteron CipherTool is an enterprise grade encryption tool that uses Crypteron's managed data encryption and key management platform to encrypt and decrypt files simply from the command line. 

## Usage Scenario 

### Black Box workflows

The typical use case is when you have sensitive data in business workflows involving "blackboxes". Blackboxes are software/systems/dataflows you don't control at a level enough to integrate directly using Crypteron's native SDKs.

In such a situation you can use Crypteron Ciphertool to secure data going in or coming out of such black boxes as files (documents, images, json, keys ... anything) from the file system. 

### Securing configuration

Applications today typically have a lot of sensitive data stored in their properties, settings or configuration file(s). These can be database connection strings (logins), password and various secrets. You can use CipherTool to protect these settings such that only your production application can decrypt the settings file, without ever storing any encryption key locally.

Visit https://www.crypteron.com to learn more or contact us at support@crypteron.com for inquiries.

## Setup

To authenticate this tool with Crypteron's data security service:

1. Register this app at https://my.crypteron.com, we do have a free trial for new customers wanting to experiment
2. Get your `AppSecret` from the Crypteron dashboard. This is a glorified API key for authentication
3. Finally, as per your security and operational practices, add the AppSecret to their
   - the environment variable `CRYPTERON_APPSECRET` OR
   - the `secrets.json` file (same location as tool). An example `secrets.json` file is:
     `{"crypteron":{"appSecret":"YourAppSecretFromDashboardGoesHere"}}`
   Crypteron CipherTool will pick it up from either location. If both are present, the environment variable is selected.

## Usage

### To Encrypt

`crypteron encrypt -i secrets.txt`

If no output file is provided, we will automatically add a `.cipher` extension to the encrypted file.

### To Decrypt

`crypteron decrypt -i secrets.txt.cipher`

If no output file is provided, we will automatically remove the `.cipher` extension if it exists on the input file. If not, you must explicitly provide the output filename

`crypteron decrypt -i secrets.txt.enc -o secrets.txt`

### CLI help

To see all the CLI options:

`crypteron <encrypt/decrypt> --help`

## Advanced Use Cases

Crypteron supports multiple applications, each with multiple security partitions and each with roles and access controls. For CipherTool, it today simply uses the default security partition's first key version with the default role and default access control rules setup. 

Contact us at support@crypteron.com to discuss any advances scenarios we can help for your business.
