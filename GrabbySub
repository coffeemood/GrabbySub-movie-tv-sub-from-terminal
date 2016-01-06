#!/bin/bash
# 06/01/16														#
# Creator(s): CoffeeMood (coffeeforthoughts@gmail.com)			#
# Contributor(s):												#
# Version: 1.0.0												#
#																#
#																#
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # 


# Usage: Just execute without arguments


####################################################################
## Process JSON file & output text file with selectable options ####

jsony () {


echo "Doing some funky stuffs....."
file=$1
array_size=$(jq '.[].href' $file | wc -l) 

#Making array from Link & Info list
array_link=($(jq '.[].href' $file | tr -d '"'))
array_list=($(jq '.[].children[].text' $file | tr ' ' '.' | tr -d '"' | paste -d "-" - - ))


for((i=0;i<$array_size;i++)); do
{
	list_Link=$(echo ${array_link[$i]})
	list_Name=$(echo ${array_list[$i]})
	echo "$list_Name+$list_Link" >> dbfile
}
done

selection dbfile
exit 0 

}


######################################################################
#### Creating a selection menu to pick subtitles with ease ###########
selection () 

{

dbfile=$1
media=("Movie" "TV")
language=("Arabian" "Chinese" "English" "French" "Spanish" "Danish" "German"  "Vietnamese") #...........
episodes=($(seq 1 $maxep))
resolution=("480p" "720p" "1080p" "OTHER")

# Take user's choices and put it in grep so the right sub is found

select movtv in ${media[@]};
do
	{
		echo "Movie or TV show?"
	case $movtv in
		"Movie")
			
			{
				echo "Please select a language for your sub"
				select line in ${language[@]};
				do
				{
			
					echo "Now select your resolution"
					select res in ${resolution[@]};
					do
						{
							case $res in 
								"480p"|"720p"|"1080p")
									select ver in $(less $dbfile | grep $line  | grep "$res");
									do
										{
											download=$(echo $ver |tr '+' '\n' | grep /subtitles)
											mrdownloader $download
											exit 0
										}
									done ;;
								
								"OTHER")
									select ver in $(less $dbfile | grep $line  );
									do
										{
											download=$(echo $ver |tr '+' '\n' | grep /subtitles)
											mrdownloader $download
											exit 0
										}
									done  ;;
							esac

						}

					done
				}
				done 
			}
				;;
		"TV" )
			 
			{
				echo "Please select a language for your sub > "
				select line in ${language[@]};
				do
				{
					echo "Now select your episode... "
					select ep in ${episodes[@]};
					do
						{
							echo "Now select your resolution"
							select res in ${resolution[@]};
							do
								{
									case $res in 
										"480p"|"720p"|"1080p")
											select ver in $(less $dbfile | grep $line | grep -e "E0$ep" | grep "$res");
											do
												{
													
													download=$(echo $ver |tr '+' '\n' | grep /subtitles)
													mrdownloader $download
													exit 0 
												}
											done ;;
										
										"OTHER")
											select ver in $(less $dbfile | grep $line | grep -e "E0$ep" );
											do
												{
													
													download=$(echo $ver |tr '+' '\n' | grep /subtitles)
													mrdownloader $download
													exit 0
												}
											done  ;;
									esac

								}
							done
						}
					done
				}
				done 
			}
				;;

	esac
	}
done 

}

############################################################################
####### Take input link and perform download, clean up db files & exit #####

mrdownloader () 

{
	downlink=$1
	echo "Downloading........."
	follow_url="http://www.subscene.com/$downlink"
	finallink=$(curl -s -L $follow_url | pup -c 'li div[class="download"] a attr{href}')
	curl -s -L -J "http://www.subscene.com/$finallink"	-O 
	ls -t | head -2 | egrep "zip|rar" | xargs unzip  >>/dev/null 2>&1
	ls -t | head -2 | egrep "zip|rar" | xargs unrar x  >>/dev/null 2>&1
	ls -t | head -2 | egrep "zip|rar" | xargs rm
	ls -t | head -2 | egrep "zip|rar" | xargs rm 
	echo "All done!"
	rm dbfile
	rm choice.txt
	exit 0 
}


	echo -n "Ok dude, what are you watching? "
	read unformatted
	formatted=$(echo $unformatted | tr ' ' '+')
	url="http://subscene.com/subtitles/title?q=$formatted&l="
	echo "Which one again? "
	select choice in $(curl -s -L $url | pup 'div[class="title"] a attr{href}');
	do
		{
			url_followed="http://subscene.com/$choice"
			curl -s -L $url_followed | pup 'tr td[class="a1"] a json{}' > choice.txt
			maxep=$(curl -s -L $url_followed | pup 'td[class="a1"] a span text{}' | head -n 5 | egrep -o "E[[:digit:]][[:digit:]]" | tr 'E' ' ')
			jsony choice.txt
			exit 0 
		}
	done 
	exit 0





 
