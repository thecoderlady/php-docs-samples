# Google Cloud Tasks Pull Queue Samples

## THIS SAMPLE IS CURRENTLY INCOMPLETE. PLEASE REFER TO [THE DOCUMENTATION](https://cloud.google.com/tasks/docs/)

Sample command-line program for interacting with the Google Cloud Tasks API.

`tasks.php` is a simple command-line program to demonstrate listing queues,
 creating tasks, and pulling and acknowledging tasks.

`src/create_task.php` is a simple function to create pull queue tasks.


## Setup:

1.  **Enable APIs** - [Enable the Cloud Tasks API](https://console.cloud.google.com/flows/enableapi?apiid=cloudtasks)
    and create a new project or select an existing project.
2.  **Download The Credentials** - Click "Go to credentials" after enabling the APIs. Click "New Credentials"
    and select "Service Account Key". Create a new service account, use the JSON key type, and
    select "Create". Once downloaded, set the environment variable `GOOGLE_APPLICATION_CREDENTIALS`
    to the path of the JSON key that was downloaded.
3.  **Clone the repo** and cd into this directory

    ```sh
    $ git clone https://github.com/GoogleCloudPlatform/php-docs-samples
    $ cd php-docs-samples/tasks
    ```
4.  **Install dependencies** via [Composer](http://getcomposer.org/doc/00-intro.md).
    Run `php composer.phar install` (if composer is installed locally) or `composer install`
    (if composer is installed globally).

## Creating a queue

To create a queue using the Cloud SDK, use the following gcloud command:

    gcloud beta tasks queues create-app-engine-queue my-appengine-queue

## Running the Samples

Set the environment variables:

Set environment variables:

First, your project ID:

    export PROJECT_ID=my-project-id

Then the queue ID, as specified at queue creation time. Queue IDs already
created can be listed with `gcloud alpha tasks queues list`.

    export QUEUE_ID=my-appengine-queue

And finally the location ID, which can be discovered with
`gcloud alpha tasks queues describe $QUEUE_ID`, with the location embedded in
the "name" value (for instance, if the name is
"projects/my-project/locations/us-central1/queues/my-pull-queue", then the
location is "us-central1").

    export LOCATION_ID=us-central1

Create a task for a queue:

    php tasks.php create-task $PROJECT_ID $QUEUE_ID $LOCATION_ID --payload=hello
