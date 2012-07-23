{exec} = require 'child_process'
fs = require 'fs'

lastChange = {}
global.coffee = []
global.less = []

# CONFIGURATION
coffee.push 'main'
less.push 'main'

coffee.src = 'source/coffee/'
coffee.dst = 'scripts/'
coffee.compress = true

less.src = 'source/less/'
less.dst = 'styles/'
less.compress = true

head = "`date -u +'%Y-%m-%d %H:%M GMT'`"
tail = "\n  created by Grifo"
# END CONFIGURATION

count = do ->
    num = 1;
    -> ('0000' + num++).slice(-4)

compile = 
    coffee: (file) ->
        coffeeFile = coffee.src + file + '.coffee'
        jsFile = coffee.dst + file + '.js'
        compress = if coffee.compress then '| uglifyjs' else ''
        exec """ 
            echo "/*
              #{head}
              #{coffeeFile} > #{jsFile}
              #{tail}
            */" > #{jsFile}
            coffee -c -p #{coffeeFile} #{compress} >> #{jsFile}
        """, (err, stdout, stderr) ->
            return console.error err if err
            console.log count() + " » Compiled #{coffeeFile}"

    less: (file) ->
        lessFile = less.src + file + '.less'
        cssFile = less.dst + file + '.css'
        compress = if less.compress then '--compress' else ''
        exec """
            echo "/*
              #{head}
              #{lessFile} > #{cssFile}
              #{tail}
            */" > #{cssFile}
            lessc #{compress} #{lessFile} >> #{cssFile}
        """, (err, stdout, stderr) ->
            return console.error err if err
            console.log count() + " » Compiled #{lessFile}"

watch = (type, file, track) ->
    try
        name = global[type].src + track + '.' + type
        fs.watch name, (event) ->
            return if event isnt 'change'
            # ignore repeated event misfires
            return if Date.now() - (lastChange[file + type] || 0) < 1000
            compile[type] file
            lastChange[file + type] = Date.now()
    catch e
        console.log "Error watching #{name}"

task 'build', 'Compile *.coffee and *.less', ->
    compile.coffee(file) for file in coffee
    compile.less(file) for file in less

task 'watch', 'Compile + watch *.coffee and *.less', ->
    # coffee
    for file in coffee
        compile.coffee(file)
        watch 'coffee', file, file
        console.log "- Wathing Coffe #{file}"
    # less
    for file in less
        compile.less(file)
        watch 'less', file, file
        console.log "- Watching Less #{file}"
        # @import
        fs.readFile less.src + file + '.less', 'utf-8', (err, content) ->
            content.replace /@import ['"](.+?)['"];/g, (all, track) ->
                return if track.match /\.css/
                track = track.replace /\.less$/, ''
                watch 'less', file, track
                console.log " + Watching Less #{track}"