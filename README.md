# MongoDB Atlas API Postman Collection

A comprehensive Postman collection for the **MongoDB Atlas Administration API v2**, providing ready-to-use API requests for managing your MongoDB Atlas clusters, projects, organizations, and more.

## Table of Contents

- [Overview](#overview)
- [What's New in v2](#whats-new-in-v2)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
  - [1. Import the Collection](#1-import-the-collection)
  - [2. Configure Authentication](#2-configure-authentication)
  - [3. Set Up Variables](#3-set-up-variables)
- [Available Endpoints](#available-endpoints)
- [Usage Examples](#usage-examples)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [Additional Resources](#additional-resources)

## Overview

This collection provides a complete set of API requests for the MongoDB Atlas Administration API v2. It includes endpoints for managing:

- **Clusters** - Create, read, update, and delete Atlas clusters
- **Projects** - Manage Atlas projects (groups)
- **Organizations** - Organization-level operations
- **Database Users** - Database user management
- **Custom Roles** - Custom database role configuration
- **IP Access List** - Network access control (formerly IP Whitelist)
- **Network Peering** - VPC/VNet peering configuration
- **Alerts & Alert Configurations** - Monitoring and alerting
- **Metrics** - Performance metrics and monitoring data
- **Teams** - Team management
- **Cloud Backups & Snapshots** - Backup and restore operations
- **Events** - Project and organization event logs
- **Private Endpoints** - Private endpoint configuration for AWS, Azure, and GCP
- **Maintenance Windows** - Schedule and manage maintenance windows
- **Serverless Instances** - Serverless instance management (Note: deprecated, migrating to Flex clusters)
- **Atlas Search** - Full-text search index management

## What's New in v2

This collection has been upgraded to use the **MongoDB Atlas Administration API v2**, which includes:

- **Versioned API**: Uses resource version headers (`application/vnd.atlas.2023-02-01+json`) for predictable API behavior
- **Updated Terminology**: "IP Whitelist" renamed to "IP Access List" following MongoDB's current naming conventions
- **Improved Stability**: Breaking changes only occur in new resource versions, with 12+ months support for older versions
- **Consistent URL Structure**: All endpoints use the `/api/atlas/v2` base path

## Prerequisites

Before using this collection, ensure you have:

1. **Postman** (Desktop app or Web version)
   - Download from [postman.com](https://www.postman.com/downloads/)
   - Supports Postman v10 and later

2. **MongoDB Atlas Account**
   - Sign up at [cloud.mongodb.com](https://cloud.mongodb.com)
   - At least one Atlas organization

3. **API Credentials** (choose one):
   - **Recommended**: Service Account with OAuth 2.0 authentication
   - **Alternative**: Programmatic API Key (Public + Private key pair)

## Getting Started

### 1. Import the Collection

**Option A: Import from File**

1. Download the `MongoDbAtlasAPICollection.postman_collection.json` file
2. Open Postman
3. Click **Import** button (top left corner)
4. Drag and drop the JSON file, or click **Upload Files** to browse
5. Click **Import** to confirm

**Option B: Import from URL**

1. In Postman, click **Import**
2. Select **Link** tab
3. Paste the raw GitHub URL to this collection
4. Click **Continue** and then **Import**

**Option C: Import from GitHub (Postman v10+)**

1. In Postman, click **Import**
2. Select **Code repository** tab
3. Connect your GitHub account and select this repository
4. Choose the collection file and click **Import**

### 2. Configure Authentication

MongoDB Atlas API supports two authentication methods:

#### Method A: API Keys with Digest Authentication (Current Setup)

1. **Create API Keys in Atlas:**
   - Log in to [Atlas](https://cloud.mongodb.com)
   - Navigate to **Organization Settings** → **Access Manager** → **API Keys**
   - Click **Create API Key**
   - Assign appropriate permissions (e.g., "Organization Owner" for full access)
   - **Save your Private Key** - it will only be shown once!
   - Add your current IP address to the API Access List

2. **Configure in Postman:**
   - Right-click the collection name → **Edit**
   - Go to the **Authorization** tab
   - Type is already set to **Digest Auth**
   - Update the following fields:

   ![Edit Auth](images/EditAuth.png)

   ```
   Username: <Your API Public Key>
   Password: <Your API Private Key>
   ```

#### Method B: Service Accounts with OAuth 2.0 (Recommended by MongoDB)

For OAuth 2.0 authentication, follow [MongoDB's Service Account documentation](https://www.mongodb.com/docs/atlas/api/api-authentication/#service-accounts).

### 3. Set Up Variables

Configure the collection variables to match your Atlas environment:

1. Right-click the collection → **Edit** (or click the three dots next to the collection name)
2. Go to the **Variables** tab

   ![Edit Variables](images/EditVariables.png)

3. Update the following variables:

   | Variable | Description | Example Value |
   |----------|-------------|---------------|
   | `base_url` | API base URL (already set) | `https://cloud.mongodb.com/api/atlas/v2` |
   | `group_id_Project0` | Your Atlas Project ID | `5e1486c6a6f2392f35072935` |
   | `org_id_TestCo` | Your Atlas Organization ID | `5e1486c6c56c986919d2680d` |

4. **Finding Your IDs:**
   - **Project ID**: In Atlas, go to your project → **Settings** → Look for "Project ID"
   - **Organization ID**: Click organization name (top left) → **Settings** → Look for "Organization ID"

5. Click **Save**

## Available Endpoints

The collection is organized into the following folders:

### Metrics
- Get all processes in a project
- Get process information
- Get database/disk lists
- Get measurements and metrics

### Clusters
- Get all clusters / Get one cluster
- Create a cluster
- Edit cluster configuration
- Delete a cluster
- Get advanced configuration options

### Projects
- Get all projects / Get one project
- Create a project

### Organizations
- Get all organizations / Get one organization
- Rename an organization
- Delete an organization
- Get organization users and projects

### Database Users
- CRUD operations for database users

### Custom Roles
- Manage custom database roles

### Project IP Access List
- Manage IP addresses allowed to connect to your clusters
- Add/update/delete access list entries
- Support for IP addresses, CIDR blocks, and AWS security groups

### Network Peering
- Manage VPC/VNet peering connections

### Alerts & Alert Configurations
- View and acknowledge alerts
- Manage alert configurations

### Teams
- Get team information

### Cloud Backups & Snapshots
- Get all cloud backup snapshots / Get one snapshot
- Take on-demand snapshots
- Get all restore jobs / Create restore job
- Get and update backup schedules

### Events
- Get project and organization events
- Track activity feed and audit trail
- Filter events by type and date

### Private Endpoints
- Manage private endpoints for AWS, Azure, and GCP
- Create and configure private endpoint services
- Secure database connections through private networks

### Maintenance Windows
- Get and update maintenance windows
- Defer maintenance operations
- Reset to default maintenance schedule

### Serverless Instances
- CRUD operations for serverless instances
- Note: Serverless instances are deprecated (sunset January 2026)
- Migration to Flex clusters recommended

### Atlas Search
- Manage full-text search indexes
- Create and configure search mappings
- Update and delete search indexes

## Usage Examples

### Example 1: List All Clusters

1. Expand **Clusters** folder
2. Click **Get All Clusters**
3. Ensure variables are set correctly
4. Click **Send**
5. View cluster information in the response

### Example 2: Add IP to Access List

1. Expand **Project IP Access List** folder
2. Click **Add Entry to Project IP Access List**
3. Modify the request body with your IP address:
   ```json
   [
     {
       "ipAddress": "203.0.113.45",
       "comment": "My office IP"
     }
   ]
   ```
4. Click **Send**

### Example 3: Create a New Cluster

1. Expand **Clusters** folder
2. Click **Create One Cluster**
3. Customize the request body with your cluster specifications
4. Click **Send**
5. Monitor the response for cluster creation status

## Troubleshooting

### Authentication Issues

**Problem:** `401 Unauthorized` responses

**Solutions:**
- Verify your API keys are correct in the Authorization tab
- Ensure your IP address is in the Organization API Access List
- Check that your API key has appropriate permissions

### Variable Issues

**Problem:** Requests fail with `404 Not Found` or invalid project/org ID

**Solutions:**
- Verify `group_id_Project0` and `org_id_TestCo` are set correctly
- Check that you're using the correct Project ID (not Project Name)
- Ensure you have access to the specified project/organization

### Rate Limiting

**Problem:** `429 Too Many Requests` responses

**Solution:**
- The Atlas API has rate limits
- Wait a moment before retrying
- Consider implementing exponential backoff in scripts

### Version Compatibility

**Problem:** Unexpected API responses or deprecated warnings

**Solution:**
- This collection uses API version `2023-02-01`
- Check [MongoDB's API Changelog](https://www.mongodb.com/docs/atlas/reference/api-resources-spec/changelog/) for updates
- Update the `Accept` header version if needed for newer features

## Contributing

Contributions are welcome! If you'd like to add missing endpoints or improve examples:

1. Fork this repository
2. Make your changes
3. Test thoroughly with your Atlas environment
4. Submit a pull request with a clear description of changes

**Please ensure:**
- All new endpoints include proper headers (Content-Type, Accept)
- Variables are used instead of hardcoded IDs
- Request/response examples are included where helpful

## Additional Resources

- [MongoDB Atlas Admin API v2 Documentation](https://www.mongodb.com/docs/api/doc/atlas-admin-api-v2/)
- [Atlas API Authentication Guide](https://www.mongodb.com/docs/atlas/api/api-authentication/)
- [Versioned API Overview](https://www.mongodb.com/docs/atlas/api/versioned-api-overview/)
- [API Changelog](https://www.mongodb.com/docs/atlas/reference/api-resources-spec/changelog/)
- [Postman Learning Center](https://learning.postman.com/)
- [MongoDB Atlas Documentation](https://www.mongodb.com/docs/atlas/)

---

**Note:** This collection uses the Atlas Administration API v2. For legacy v1 API endpoints, please refer to older versions of this collection.

**Last Updated:** January 2025
