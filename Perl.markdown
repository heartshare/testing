### Perl

```perl
our $baseoid = '.1.3.6.1.4.1.7460.1.12';
...
our $nametoindex = {
    'questions' =>              ['101.1', 'string'],
    'tcp-questions' =>          ['101.2', 'string'],
    'cache-entries' =>          ['101.3', 'string'],
    '...' => [],
}
while (my $cmd = <STDIN>) {
    chomp $cmd;
    if ($cmd eq 'PING') {
        print "PONG\n";
    }
    ...
}
sub update_recursor_mib {
    my $reccont = new FileHandle "$rec_control get @statistics|";
    ...
    while ( my $line = <$reccont> ) {
        ...
    }
    return $newmibtree;
}


