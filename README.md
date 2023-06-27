&nbsp;

<p align="center">
  &nbsp;
  <a href="https://sourcify.dev"><img src="https://raw.githubusercontent.com/sourcifyeth/assets/master/logo-assets-svg/logoText.svg" alt="sourcify logo" role="presentation"></a>
</p>

[![codecov](https://codecov.io/gh/ethereum/sourcify/branch/staging/graph/badge.svg?token=eN6XDAwWfV&flag=server)](https://codecov.io/gh/ethereum/sourcify)

Sourcify ([sourcify.dev](https://sourcify.dev)) is a Solidity source code and [metadata](https://docs.sourcify.dev/docs/metadata/) verification tool.

The project aims to serve as an infrastructure for other tools with an [open repository](https://docs.sourcify.dev/docs/repository/) of verified contracts as well as an [API](https://docs.sourcify.dev/docs/api/) and other services. The goal is to make contract interactions on the blockchain safer and more user friendly with open sourced contract codes, contract ABI, and [NatSpec](https://docs.soliditylang.org/en/latest/natspec-format.html) comments available via the contract metadata.

_ℹ️ [This monorepo](https://github.com/ethereum/sourcify) contains the main services and the verification UI. The [sourcifyeth Github organization](https://github.com/sourcifyeth) contains all other auxiliary services and components._

## Documentation

For more details refer to [docs.sourcify.dev](https://docs.sourcify.dev/docs/intro/)

## Questions?

🔍 Check out docs [F.A.Q.](https://docs.sourcify.dev/docs/faq/) and use search in docs.

💬 Chat with us on [Gitter](https://gitter.im/ethereum/source-verify) or [Matrix chat](https://matrix.to/#/#ethereum_source-verify:gitter.im)

🐦 Follow us and help us spread the word on [Twitter](https://twitter.com/SourcifyEth).

## Adding a new chain

If you'd like to add a new chain support to Sourcify please follow the [chain support instructions](https://docs.sourcify.dev/docs/chain-support/) in docs.


## Hosting the Project on AWS

To efficiently host your project on AWS, it is recommended to utilize the "t2.medium" or "t2.small" EC2 instance types, as they can help reduce Docker build time and improve overall performance.

Here's a step-by-step guide on how to set up your project on AWS:
 1. **Launch an EC2 Instance:**
   
   - Configure other instance details like VPC, subnet, security groups, etc., according to the needs.
   - Generate a key pair to securely access the EC2 instance via SSH.

2. **SSH into the EC2 Instance:**
   - Use the generated key pair to establish an SSH connection with the EC2 instance. For example:
     ```
     ssh -i your_key_pair.pem ec2-user@your_ec2_instance_public_dns
     ```

3. **Run the Startup Script:**
   - Run These Commands 
     ```bash
     
     # Install Docker
     sudo yum install -y docker
     
     # Install Git
     sudo yum install -y git
     
     # Clone the repository
     git clone https://github.com/modularcloud/sourcify.git
     
     # Change to the cloned directory
     cd sourcify
     
     # Start Docker service
     sudo service docker start
     
     # Build the Docker image
     sudo docker build -t sourcify:1.0 -f src/Dockerfile.server .
     
     # Run the Docker container
     sudo docker run -d -p 80:5555 sourcify:1.0
     ```

4. **Run the Application:**
   - Once the commands has  completed successfully, your application will be attached to port 80 of the AWS EC2 instance, which is the default port for HTTP traffic.
   - Access your application by entering the EC2 instance's public DNS or IP address into a web browser. For example:
     ```
     http://your_ec2_instance_public_dns
     ```

    By following these steps, you will be able to host your project on AWS using an EC2 instance

 5. **Start Verifying Contracts :**
   - To verify the contract, you can use the following URL: `http://your_ec2_instance_public_dns/verify`
   - Refer to the [Sourcify documentation](https://docs.sourcify.dev/docs/intro/) for more details on contract verification.



