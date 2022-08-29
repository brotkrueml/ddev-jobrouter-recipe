# Use JobRouter® 5.2 with ddev

**Note:** This recipe uses JobRouter® 5.2 without the Windows services by now. This
is sufficient for a development system, as you can start instances via the simulator,
call the REST API or develop PHP system activities. You also need a valid
license file for using this installation.

> When updating from a JobRouter® 5.1 installation you can use the same ddev configuration.

## Configure ddev

1. Use the `ddev config --project-type=php --php-version=7.4` command to configure the project.
   Check the generated configuration in `.ddev/config.yaml`, especially the ports.
   You can find an example configuration file in the corresponding JobRouter® version folder.
2. Copy the content of the [according JobRouter® version](.) from this repository into your `.ddev` folder.
3. Unpack the JobRouter® zip installation file into the `public` folder.
4. Start the Docker containers with `ddev start`. The first start can last some minutes 
   because the web container is build.
5. Call the configured URL in your browser which starts the setup.

You can use the default database credentials:
- Host: `db`
- Database name: `db`
- Username: `db`
- Password: `db`

> If you want to use ElasticSearch, you can follow this 
> [recipe](https://github.com/drud/ddev-elasticsearch).
> Please also refer to the relevant section in the JobRouter® installation manual.