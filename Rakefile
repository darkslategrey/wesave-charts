namespace :package do
  desc 'Cleanup .deploy directory'
  task :cleanup do
    sh 'rm -f .deploy/*'
  end

  desc 'Package all charts into ".deploy" dir'
  task all: ['package:cleanup'] do
    sh 'helm package charts/* --destination .deploy'
  end

  desc 'Package welearn-back'
  task welean: ['package:cleanup'] do
    sh 'helm package charts/welearn-back --destination .deploy'
  end
end

desc 'Build packages charts/* charts into .deploy'
task :packages do
  sh 'helm package charts/{elasticsearch,postgresql,redis,welearn-back} --destination .deploy'
end

desc 'Release charts'
task :release do
  sh 'cr upload -o darkslategrey -r wesave-charts -p .deploy --config ~/.cr.yaml'
end

desc 'Create index.yaml file'
task :index do
  sh 'cr index -c https://darkslategrey.github.io/wesave-charts/ -i ./docs/index.yaml -p .deploy -o darkslategrey -r wesave-charts'
end
