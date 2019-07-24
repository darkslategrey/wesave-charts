


desc 'Build packages charts/* charts into .deploy'
task :packages do
  sh 'helm package charts/{elasticsearch,postgresql,redis} --destination .deploy'
end

desc 'Release charts'
task :release do
  sh 'cr upload -o darkslategrey -r wesave-charts -p .deploy --config ~/.cr.yaml'
end

desc 'Create index.yaml file'
task :index do
  sh 'cr index -c https://darkslategrey.github.io/wesave-charts/ -i ./docs/index.yaml -p ../.deploy -o darkslategrey -r wesave-charts'
end
