#!/usr/bin/env rake

require 'hoe'

Hoe.plugin :hg
Hoe.plugin :yard
Hoe.plugin :signing

Hoe.plugins.delete :rubyforge

hoespec = Hoe.spec 'linguistics' do
	self.name = 'linguistics'
	self.readme_file = 'README.md'
	self.history_file = 'History.md'

	self.developer 'Michael Granger', 'ged@FaerieMUD.org'

	self.extra_dev_deps.push *{
		'rspec'      => '~> 2.4.0',
		'linkparser' => '~> 1.1.0',
		'wordnet'    => '~> 0.99.0',
	}

	self.spec_extras[:licenses] = ["BSD"]
    self.spec_extras[:signing_key] = '/Volumes/Keys/ged-private_gem_key.pem'
	self.spec_extras[:post_install_message] = [
			"This library also presents tie-ins for the 'linkparser' and",
			"'wordnet' libraries, which you can enable by installing the",
			"gems of the same name."
		  ].join( "\n" )

	self.require_ruby_version( '>=1.9.2' )
	self.hg_sign_tags = true if self.respond_to?( :hg_sign_tags= )
	self.yard_opts = [ '--use-cache', '--protected', '--verbose' ] if
		self.respond_to?( :yard_opts= )
end

ENV['VERSION'] ||= hoespec.spec.version.to_s

