# HealthSampleData

Sample health data sources for a variety of health formats and use cases.
Uses the wonderful [DataDeps.jl](https://github.com/oxinabox/DataDeps.jl) package to automatically download, hash, and manage the download for you.

# Provided Data Sources

## Observational Medical Outcomes Partnership Common Data Model (OMOP CDM)

**Source Description:** The Observational Medical Outcomes Partnership (OMOP) was created in 2009 to reach consensus on data types, study designs, and privacy concerns while sharing data.
An important output of OMOP is the OMOP Common Data Model (OMOP CDM) which is an effort to standardize observational data to enable transferable analysis. [@overhage2012validation]
The OMOP CDM features person­centric design where each domain records personal identity while prioritizing data protection through the limiting of information that could endanger patient anonymity.
The CDM itself does not require a specific technology to work with the data stored in this standard.

Available OMOP CDM data sources:

 - **Eunomia** - Synthetic OMOP CDM data generated by Synthea available in a single sqlite file.

# Instructions

## Ingesting Data into PostgreSQL

Install postegre
https://www.digitalocean.com/community/tutorials/how-to-install-postgresql-on-ubuntu-22-04-quickstart
install postegre client
sudo apt install postgresql-client
Added cedar prince to ubuntu
sudo adduser thecedarprince
sudo usermod -aG sudo thecedarprince
Added password
Switched to it
su - thecedarprince
In postegre added user and database
psql -d synthea;
Delete the synthea database from within PostgreSQL
Connect to your default database
Do something like DROP DATABASE synthea;
Confirm that
Create a user called thecedarprince
Do CREATE ROLE thecedarprince SUPERUSER;
Create the synthea database again by doing:
CREATE DATABASE synthea
Switched role
In terminal
sudo -u postgres psql -c "ALTER ROLE thecedarprince WITH LOGIN;"
In psql
ALTER USER thecedarprince PASSWORD 'password'
type
sudo -i -u postgres
then from separate window where logged as thecedarprince (synthea.dump need to be in thecedarprince home direcory )
pg_restore -C -d db < /home/thecedarprince/synthea.dump

