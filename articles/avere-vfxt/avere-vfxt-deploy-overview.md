---
title: Deployment overview - Avere vFXT for Azure 
description: Overview of deploying Avere vFXT for Azure
author: ekpgh
ms.service: avere-vfxt
ms.topic: conceptual
ms.date: 02/20/2019
ms.author: rohogue
---

# Avere vFXT for Azure - deployment overview

This article gives an overview of the steps needed to get an Avere vFXT for Azure cluster up and running.

Several tasks are needed before and after you create the vFXT cluster from the Azure Marketplace. Having a clear sense of the start-to-finish process will help you scope the effort needed. 

## Deployment steps

After [planning your system](avere-vfxt-deploy-plan.md), you can begin to create your Avere vFXT cluster. 

An Azure Resource Manager template in the Azure Marketplace collects the necessary information and automatically deploys the entire cluster. 

After the vFXT cluster is up and running, you will want to know how to connect clients to it and, if necessary, how to move your data to the new Blob storage container.  

Here is an overview of all of the steps.

1. Configure prerequisites 

   Before creating a VM, you must create a new subscription for the Avere vFXT project, configure subscription ownership, check quotas and request an increase if needed, and accept terms for using the Avere vFXT software. Read [Prepare to create the Avere vFXT](avere-vfxt-prereqs.md) for detailed instructions.

1. Create the Avere vFXT cluster 

   Use the Azure Marketplace to create the Avere vFXT for Azure cluster. A template collects the required information and executes scripts to create the final product.

   Cluster creation involves these steps, which are all done by the marketplace template: 

   * Creating new network infrastructure and resource groups, if needed
   * Creating a *cluster controller*  

     The cluster controller is a simple VM that resides in the same virtual network as the Avere vFXT cluster and has the custom software needed to create and manage the cluster. The controller creates the vFXT nodes and forms the cluster, and it also provides a command-line interface to manage the cluster during its lifetime.

     If you create a new vnet during the deployment, your controller will have a public IP address. This means the controller can serve as a jump host for connecting to the cluster from outside the vnet.

   * Creating the cluster node VMs

   * Configuring the cluster node VMs to form the cluster

   * Optionally, creating a new Blob container and configuring it as back-end storage for the cluster

1. Configure the cluster 

   Connect to the Avere vFXT configuration interface (Avere Control Panel) to customize the cluster's settings. Opt in for support monitoring, and add your storage system if you are using an on-premises data center.

   * [Access the vFXT cluster](avere-vfxt-cluster-gui.md)
   * [Enable support](avere-vfxt-enable-support.md)
   * [Configure storage](avere-vfxt-add-storage.md) (if needed)

1. Mount clients

   Follow the guidelines in [Mount the Avere vFXT cluster](avere-vfxt-mount-clients.md) to learn about load balancing and how client machines should mount the cluster.

1. Add data (if needed)

   Because the Avere vFXT is a scalable multi-client cache, the best way to move data to a new back-end storage container is with multi-client, multithreaded file copy strategy. Read [Moving data to the vFXT cluster](avere-vfxt-data-ingest.md) for details.

## Next steps

Continue to [Prepare to create the Avere vFXT](avere-vfxt-prereqs.md) to complete the preliminary tasks for deploying the Avere vFXT for Azure. 