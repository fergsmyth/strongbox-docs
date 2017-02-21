Cron tasks can be used to execute scheduled tasks.

Cron tasks can execute tasks against:
- A path in a repository
- A repository
- All the repositories in a storage
- All repositories

# Implementations

The following implementations exist:
* Java
* Groovy

All the built-in cron tasks are written in Java, however, it is also possible to execute scheduled Groovy scripts.

# Available Cron Tasks

The following is a list of the implemented cron tasks.

## Rebuild Maven Metadata

Sometimes Maven metadata can become corrupt, or not reflect the actual artifacts on the file system. Usually, this will happen in cases where an artifact has been added, from the file system manually and the respective `maven-metadata.xml` files have not been updated.

This cron task can rebuild the metadata for Maven repositories. (Check this article for more information on [[Maven Metadata]]).

## Rebuild Maven Indexes

Sometimes Maven indexes can become corrupt, or not reflect the actual artifacts on the file system. Usually, this will happen in cases where an artifact has been added, or removed from the file system manually, in which case the index would not be updated on it own, because the application would know of this change.

This cron task can rebuild the Lucene for Maven repositories. (Check this article for more information on [[Maven Indexer]]).

## Download Remote Indexes (Maven Repositories Only)

Maven proxy repositories have two types of Lucene indexes:
* A local one, that contains all the locally cached artifacts.
* A remote one, that contains a list of all of the artifacts available from the remote.

Each proxy repository needs to have a cron task that downloads the remote at a given interval and merges it with the local copy of the remote.

## Empty Trash

This task can periodically empty the trash.

## Remove Released Snapshots

This task checks which artifacts have been released and can be removed from the respective snapshot repository.

## Regenerate Checksums

This task can be useful, in cases where an artifact has been copied to (or altered) manually on the file system and there are no checksum, or the checksum has become invalid.

# Information for developers

## Location Of Code
The code for the cron tasks is located under the [strongbox-cron-tasks](https://github.com/strongbox/strongbox/tree/master/strongbox-cron-tasks) module.

The base cron implementation classes are:
* [JavaCronJob](https://github.com/strongbox/strongbox/blob/master/strongbox-cron-tasks/src/main/java/org.carlspring.strongbox/cron/api/jobs/JavaCronJob.java)
* [GroovyCronJob](https://github.com/strongbox/strongbox/blob/master/strongbox-cron-tasks/src/main/java/org.carlspring.strongbox/cron/api/jobs/GroovyCronJob.java)

## Notes

// TODO: Explain the Spring context lookup magic here

// TODO: Explain how to run the cron tests


# See Also
* [[Maven Metadata]]
* [[Maven Indexer]]
* [[REST API]
* [[Storages]]
* [[Repositories]]