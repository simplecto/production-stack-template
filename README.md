# Purpose

This is a general template that I use for every new project.
If you follow my blog (simplecto.com) then you will know that
I am a big believer in Django and a supporting ecosystem around
that framework.

Principles
  * 12-factor ready
  * Simplicity, with a path forward for scaling the parts you need.
  * Single developer friendly
  * Single machine friendly
  * Optimize for developer speed

Docker
  * building and running locally
  * building and running remotely
  * pushing to private repo
  * docker-compose local
  * docker-compose production
    * with docker labels
    

Django
  * my patterns for config/ folder
  * pickup environment vars from `.env` in `settings.py` file
  * support libraries (see blog)
  * 

Minimal Javascript (because I dont like it)
  * This is a personal thing. 

Traefik configuration for the reverse proxy
Extras
  * Twilio
  * sentry
  * Sendgrid
  * Makefiles for CLI Productivity
  * how I like to setup pycharm for local debugging  
  
Other blueprints/cookie-cutters
  * mention cookie cutter
  * pydanny
  * does awesome cookie-cutter exist?
  
Future considerations:
  * include a risk assessment for ISO 27001 / 27005 level applications
  * include ansible / cloud-init scripts for standing up the hosting server
  * 
  
Video / instructions on how to setup pycharms with screenshots

Patterns

  * Skip celery. Use a database and django commands as reliable, robust, and easily understood workers
    * their work would become indepotend
    
  