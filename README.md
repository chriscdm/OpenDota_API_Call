# OpenDota_API_Call

This is a short project demonstrating some of the processes of a data pipeline on a relatively small scale.

For this project I looked at Dota 2 professional matches using data from the OpenDota.com API. Open Dota is a website that provides players with large amount of data regarding both public and professional matches and they have a well documented API with a free tier.

Notebook 00:

This notebook collects data on every single professional match to date. The API call I used provides a JSON with data on 100 professional matches and I iterated backwards until every match had been collected and stored in a pandas dataframe.

Though not strictly necessary for a project of this scope, I set up a MySql server on Amazon Web Services to store the data (in addition to storing it on my laptop). I used the sqlalchemy package to send my pandas dataframe to the server and store it as a table and I used .pickle to store the pandas python object on my laptop locally.

Notebook 01:

This notebook updates the match list by checking for the most recent match in my dataframe and calling the API until that match is found. Once the match is found the data is stored both locally and on the MySql server. In both cases the master list is updated and a timestamped backup version is created.

Notebook 02:

In this notebook the master list is imported (it works to import from either my local hard drive or from AWS) and some very basic cleaning is done along with generating some visuals.

Next steps:

The next step would be to create a functional python script and fully automate the update process on an EC2 instance which would then be connected to the MySql database. This process could be set to run daily.
