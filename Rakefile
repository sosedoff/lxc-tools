FILES = [
  'lxc-setup-container',
  'lxc-setup-network',
  'lxc-setup-rootfs'
]

task :install do
  dir = File.dirname(__FILE__)
  target = '/usr/local/bin'

  FILES.each do |name|
    puts "Installing #{name}"
    script = File.join(dir, name)
    `cp #{script} #{target}/#{name}`
  end
end