# Host Sites Block on pfSense

This guide provides instructions on how to block specific host sites using pfSense, an open-source firewall/router software distribution.

## Prerequisites

- A running instance of pfSense.
- Administrative access to the pfSense web interface.

## Steps to Block Host Sites

### 1. Access pfSense Web Interface

1. Open a web browser and navigate to the IP address of your pfSense firewall.
2. Log in with your administrative credentials.

### 2. Create an Alias for Blocked Sites

1. Navigate to **Firewall** > **Aliases**.
2. Click on the **Add** button to create a new alias.
3. Set the following fields:
   - **Name**: `BlockedSites`
   - **Description**: `List of blocked host sites`
4. In the **Type** dropdown, select `Host(s)`.
5. Add the hostnames or IP addresses of the sites you want to block in the **Host(s)** field.
6. Click **Save** and then **Apply Changes**.

### 3. Create a Firewall Rule to Block the Sites

1. Navigate to **Firewall** > **Rules**.
2. Select the interface (e.g., LAN) where you want to apply the block.
3. Click on the **Add** button to create a new rule.
4. Set the following fields:
   - **Action**: `Block`
   - **Interface**: `LAN` (or the appropriate interface)
   - **Address Family**: `IPv4`
   - **Protocol**: `Any`
5. In the **Source** section, set the following:
   - **Source**: `Any`
6. In the **Destination** section, set the following:
   - **Destination**: `Single host or alias`
   - **Destination Address**: `BlockedSites` (the alias created earlier)
7. Add a description for the rule, such as `Block access to specific host sites`.
8. Click **Save** and then **Apply Changes**.

### 4. Verify the Block

1. Try to access one of the blocked sites from a device on the LAN network.
2. The site should be inaccessible, confirming that the block is working.

## Troubleshooting

- Ensure that the alias contains the correct hostnames or IP addresses.
- Verify that the firewall rule is placed correctly in the rule order.
- Check the pfSense logs for any errors or issues related to the rule.

## Conclusion

By following these steps, you should be able to block specific host sites on your network using pfSense. This can help in managing and securing your network by preventing access to unwanted or harmful sites.

## References

- [pfSense Documentation](https://docs.netgate.com/pfsense/en/latest/)
- [pfSense Forum](https://forum.netgate.com/)
