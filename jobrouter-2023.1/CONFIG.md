# Use JobRouter® 2023.1 with ddev

**Note:** This recipe uses JobRouter® 2023.1 without the Windows services by now. This
is sufficient for a development system, as you can start instances via the simulator,
call the REST API or develop PHP system activities. You also need a valid
license file for using this installation.

## Configure ddev

1. Use the `ddev config --project-type=php --php-version=8.1` command to configure the project.
   Check the generated configuration in `.ddev/config.yaml`, especially the ports.
   You can find an example configuration file in the corresponding JobRouter® version folder.
2. Copy the content of the [according JobRouter® version](.) from this repository into your `.ddev` folder.
3. Unpack the JobRouter® zip installation file into the `public` folder.
4. Rename `public/.htaccess-jobrouter` to `public/.htaccess`
5. Start the Docker containers with `ddev start`. The first start can last some minutes
   because the web container is build.
6. Call the configured URL in your browser which starts the setup.

You can use the default database credentials:
- Host: `db`
- Database name: `db`
- Username: `db`
- Password: `db`

> If you want to use ElasticSearch, you can follow this
> [recipe](https://github.com/drud/ddev-elasticsearch).
> Please also refer to the relevant section in the JobRouter® installation manual.