=head1 host08.perl6.com - home of camelia, the IRC eval bot

host0. is run by diakopter, though moritz also has root access.

It is a bit beefier than feather, and thus is also used for smoking Perl 6
modules on rakudo.

=head2 Camelia

Camila runs as the user C<p6eval> in C</home/p6eval>. The actual code is
C</home/p6eval/evalbot>, source from https://github.com/perl6/evalbot.

The home directory is littered with builds of the various compilers that
camelia can use. Those that are updated regularly are built from cron scripts
(cron os user p6eval). Most build scripts are under version control together
with the actual evalbot.

=head3 perl6-j

The C<perl6-j> (Rakudo on the JVM) is handled a bit special, because it uses a
pre-launched eval server (startup time too high). The eval server runs as user
C<pp6eval_eval>; if it hangs, kill all perl6 and java processes the belong to
user p6eval_eval, and then as that user, run

    nohup perl /home/p6eval/evalbot/runtime/run-rakudo-jvm-evalserver &

=head2 Ecosystem smoke reports

Available on the web as L<http://host08.perl6.com:8080/report>.

The web server runs as user L<emmentaler>. To start it, log in as that user,
start a new tmux session

    $ tmux

and then

    $ cd ~/tools/SmokeResults/
    $ starman --port 8080 bin/app.pl

And press C<C-b d> (that is, Ctrl+b followed by a "d") to detach the tmux
session.

The actual smoke data is supplied by colomon.
