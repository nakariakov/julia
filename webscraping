using JSON, Requests
url = "https://www.reddit.com/r/Julia/"
firstrequest = get("$(url)/.json")

jd = JSON.parse(Requests.text(firstrequest))

after = jd["data"]["after"]
counter = length(jd["data"]["children"])

c = []
for i in 1:counter
    url = jd["data"]["children"][i]["data"]["url"]
    id  = jd["data"]["children"][i]["data"]["id"]
    title  = jd["data"]["children"][i]["data"]["title"]
    author  = jd["data"]["children"][i]["data"]["author"]
    flair = jd["data"]["children"][i]["data"]["link_flair_css_class"]
    created = jd["data"]["children"][i]["data"]["created"]
    push!(c, (url, id, title, author, flair, created))
end

for post in c
    println(post[3])
    println(" ", post[4])
    println(" ", Dates.unix2datetime(post[6]))
end
