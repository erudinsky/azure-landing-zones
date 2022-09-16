## Introduction 

This folder contains resources for policy as code management in Azure written in Bicep lang.

```bash

├── README.md                             => you are here!
├── assignment.bicep                      => module for policy and service principals (for dine effect) assignments
├── custom                                => folder with custom policy definitions
│   ├── a_tag_policy.json                 => simple policy to flag lack of tag on resource
│   ├── allowed_location.json             => allowed locations of resources for the scope
│   └── enable_mdc_on_subscription.json   => enables Microsoft Defender for Cloud (if not yet)
├── main.bicep                            => main bicep template
├── main.parameters.dev.json              => main bicep parameters file
└── wrapper.bicep                         => additional step for nested loops

```

## How to execute

Review `main.parameters.dev.json` and adjust accordingly. Get your tenantID (root management group ID) if you plan to deploy to it, otherwise get mg ID for target of your deployment. Make sure you have logged in with your az cli and have permissions to create policy definition, policy assignment and role assignment.

```bash 

cd policies

# `mg_id` should be replaced either with GUID formatted tenantId or Id of Management Group for deployment.
az deployment mg create -n policyDeployment -f main.bicep -p main.parameters.dev.json -m <mg_id>

```

Review deployment in Azure Portal > Management Groups > Policy.