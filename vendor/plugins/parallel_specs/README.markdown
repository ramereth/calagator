Rake tasks to run specs in parallel, to use multiple CPUs and speedup test runtime.

Setup
=====

    script/plugin install git://github.com/grosser/parallel_specs.git

Copy your test environment inside `config/database.yml` once for every cpu you got ('test'+number).

    test:
      adapter: mysql
      database: xxx_test
      username: root

    test2:
      adapter: mysql
      database: xxx_test2
      username: root

For each environment, create the databases
    mysql -u root -> create database xxx_test2;

Run like hell :D

    (Make sure your `spec/spec_helper.rb` does not set `ENV['RAILS_ENV']` to 'test')

    rake spec:parallel:prepare[2] #db:reset for each env

    rake spec:parallel[1] --> 86 seconds
    rake spec:parallel    --> 47 seconds (default = 2)
    rake spec:parallel[4] --> 26 seconds
    ...

Example output
--------------

    running specs in 2 processes
    93 specs per process
    starting process 1
    starting process 2
    ... test output ...
    Took 47.319378 seconds


TODO
====
 - find out how many CPUs the user has
 - sync the output, so that results do not appear all at once
 - grab the 'xxx examples ..' line and display them at the bottom
 - find a less hacky approach (without manual creation so many envs)


Author
======
inspired by [pivotal labs](http://pivotallabs.com/users/miked/blog/articles/849-parallelize-your-rspec-suite)
[Michael Grosser](http://pragmatig.wordpress.com)
grosser.michael@gmail.com
Hereby placed under public domain, do what you want, just do not hold me accountable...