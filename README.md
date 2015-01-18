2014.drupalcampwroclaw.pl
=========================

Static archive of drupalcamp wroclaw website for 2014

Just to make sure that these websites never get lost to the community, we create static archive of them and host them on gh-pages, where they are available to everyone.

Everyone can clone, fork etc


Created with httrack

# Download website but avoid endless links on calendar views
httrack http://www.drupalcampwroclaw.pl -O . -N "%h%p/%n/index%[page].%t" -WqQ%v --robots=0  \

-*node/70/2014-05-14* \

-*node/70/2014-05-15* \

-*node/70/2014-05-16* \

-*node/70/2014-05-17* \

-*node/70/2014-05-18* \

-*node/70/2014-05-19* \

-*sessions-accepted-calendar/70/2014-05-14* \

-*sessions-accepted-calendar/70/2014-05-15* \

-*sessions-accepted-calendar/70/2014-05-16* \

-*sessions-accepted-calendar/70/2014-05-17* \

-*sessions-accepted-calendar/70/2014-05-18* \

-*sessions-accepted-calendar/70/2014-05-19* \

#
#Fix paths and all
#
# move index to top

cp ./www.drupalcampwroclaw.pl/index/index.html ./www.drupalcampwroclaw.pl/

rm -r ./www.drupalcampwroclaw.pl/index

# intex.html to slash

find ./www.drupalcampwroclaw.pl/ -name "*.html" -type f -print0 | xargs -0 perl -i -pe "s/\/index.html/\//g"

find ./www.drupalcampwroclaw.pl/ -name "*.html" -type f -print0 | xargs -0 perl -i -pe "s/\/index-[0-9].html/\//g"

# change relative links (../../) to absolute(/)

find ./www.drupalcampwroclaw.pl/ -name "*.html" -type f -print0 | xargs -0 perl -i -pe "s/\/\.\.//g"

find ./www.drupalcampwroclaw.pl/ -name "*.html" -type f -print0 | xargs -0 perl -i -pe "s/\.\.//g"

# disable google analytics

find ./www.drupalcampwroclaw.pl/ -name "*.html" -type f -print0 | xargs -0 perl -i -pe "s/UA-46199836-1/XX-XXXXXXXX/g"

# change links to front page from /index/ to /

find ./www.drupalcampwroclaw.pl/ -name "*.html" -type f -print0 | xargs -0 perl -i -pe "s/href=\"\/index\/\"/href=\"\/\"/g"



