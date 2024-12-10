brew cask install dwarf-fortress  			# https://brewinstall.org/install-dwarf-fortress-mac-osx/
cd /usr/local/Caskroom/dwarf-fortress/0.47.04/df_osx	# after brew cask install
xattr -r -d com.apple.quarantine ./        		# https://tips.applenws.com/getting-started-with-the-game-dwarf-fortress-on-your-mac/2019/youtube
# expected error: xattr: No such file: .//libs/SDL_image.framework/Frameworks
./df

