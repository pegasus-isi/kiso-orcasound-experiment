This workflow is based on an open-source software and hardware project that trains itself using the audio files generated via the hydrophone sensors deployed in three locations in the state of Washington (San Juan Island, Point Bush, and Port Townsend) in order to study Orca whales in the Pacific Northwest region. This workflow uses code and ideas available in the Orcasound GitHub actions workflow and the Orca Hello real-time notification system. The Kiso experiment runs the Orcasound workflow workflow.

# Getting Started

> [!IMPORTANT]
> The experiment can't be run on ARM-based machines.

## Prerequisites

```sh
pip install kiso
pip install kiso[vagrant]
```

## Credentials

Create a file named `secrets/credentials.conf` with the following content:

```ini
[amazon]
endpoint = https://s3.<AWS-REGION>>.amazonaws.com/

[george@amazon]
access_key = <AWS-ACCESS-KEY>
secret_key = <AWS-SECRET-KEY>
```

## Running the experiment


```sh
# Check Kiso experiment configuration
kiso check

# Provision and setup the resources
kiso up

# Run the experiments defined in the experiment configuration YAML file
kiso run

# Destroy the provisioned resources
kiso down

# Pegasus workflow submit directories will be placed in the output directory at the end of the experiment. The submit directories will also have a statistics directory with the pegasus-statistics output.
# Outputs defined in the experiment configuration will be placed to the destination specified in the experiment configuration.
```

# Versioning

```sh
pip install commitizen

# Committing changes
# Use git cz c or cz c to commit changes

# Tagging a new version, updating the changelog
cz bump
git push --tags

# Use GitHub CLI to create a new release
# gh release create --repo <user-or-org>/<repo> <tag-name>
```

# References

- [Pegasus Workflow Management System](https://pegasus.isi.edu)
- [EnOSlib](https://discovery.gitlabpages.inria.fr/enoslib/)

# Acknowledgements

Kiso is funded by National Science Foundation (NSF) under award [2403051](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2403051).
