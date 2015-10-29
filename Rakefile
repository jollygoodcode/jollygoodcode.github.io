require "pathname"

desc "rake new_post [post_name]"
task :new_post do
  name = ARGV.last
  task name.to_sym do; end

  create_post(dasherize_file_name(name), "_posts/")
end

def dasherize_file_name(str)
  str.downcase.gsub("&lt;", "<").gsub(/[^\w<>#?!$]+/, "-")
end

def create_post(post_name, directory)
  filename = "#{Time.now.utc.strftime("%Y-%m-%d")}-#{post_name}.md"
  path = Pathname(directory + filename)

  if path.exist?
    puts "'#{path}' already exists."
  else
    path.write content
    `$EDITOR #{path}`
    puts "Created: #{path}"
  end
end

def content
  content = <<-TEMPLATE.gsub(/^ */, "".freeze)
    ---
    title: "Enter a concise title."
    date: "#{Time.now.utc.strftime("%Y-%m-%dT%H:%M:%S")}"
    permanent_url: "https://github.com/jollygoodcode/jollygoodcode.github.io/issues/"
    description: ""
    ---
  TEMPLATE
end
