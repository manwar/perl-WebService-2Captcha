# NAME

WebService::2Captcha - Blah blah blah

# SYNOPSIS

    use WebService::2Captcha;

    my $w2c = WebService::2Captcha->new(
        key => '......', # from https://2captcha.com/setting
    );

    my $b = $w2c->getbalance() or die $w2c->errstr;
    print "Balance: $b\n";

    my $res = $w2c->decaptcha("$Bin/captcha.png", language => 1) or die $w2c->errstr;
    print "Got text as " . $res->{text} . "\n";
    if (0) {
        $w2c->reportbad($res->{id}) or die $w2c->errstr;
    }

# DESCRIPTION

WebService::2Captcha is for [https://2captcha.com/setting](https://2captcha.com/setting)

# METHODS

## decaptcha

    my $res = $w2c->decaptcha($filename_or_file_content) or die $w2c->errstr;
    my $res = $w2c->decaptcha(
        $filename_or_file_content
        phrase => 1,
        language => 1, # check https://2captcha.com/setting
    ) or die $w2c->errstr;

    print "Got text as " . $res->{text} . "\n";
    if (0) {
        $w2c->reportbad($res->{id}) or die $w2c->errstr;
    }

## upload

    my $captcha_id = $w2c->upload($filename_or_file_content) or die $w2c->errstr;
    my $captcha_id = $w2c->upload(
        $filename_or_file_content
        phrase => 1,
        language => 1, # check https://2captcha.com/setting
    ) or die $w2c->errstr;

## get

    my $text = $w2c->get($captcha_id) or die $w2c->errstr;

## get\_multi

    my @texts = $w2c->get_multi($captcha_id1, $captcha_id2) or die $w2c->errstr;

## getbalance

    my $b = $w2c->getbalance() or die $w2c->errstr;
    print "Balance: $b\n";

## reportbad

    my $res = $w2c->reportbad($captcha_id) or die $w2c->errstr;

## getstats

    my $res = $w2c->getstats($date) or die $w2c->errstr;

## load

    my $load = $w2c->load();

## request

    my $res = $w2c->request(action => 'getstats', date => $date);

underlaying method to build request

# AUTHOR

Fayland Lam <fayland@gmail.com>

# COPYRIGHT

Copyright 2014- Fayland Lam

# LICENSE

This library is free software; you can redistribute it and/or modify
it under the same terms as Perl itself.

# SEE ALSO
