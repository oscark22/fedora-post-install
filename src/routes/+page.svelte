<script lang="ts">
	import Paragraph from "$lib/comps/paragraph.svelte";
	import Subtitle from "$lib/comps/subtitle.svelte";
	import Image from "$lib/comps/image.svelte";
	import CodeSnippet from "$lib/comps/code-snippet.svelte";
	import random_doggo from "$lib/images/random_doggo.jpg";
	import Title from "$lib/comps/title.svelte";
	import ParagraphItalic from "$lib/comps/paragraph-italic.svelte";
	import Redirect from "$lib/comps/redirect.svelte";
</script>

<svelte:head>
	<title>Fedora Post-Install</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<div class="font-sans antialiased text-slate-800">
	<nav class="flex bg-slate-100 px-4 py-3 justify-end">
		<div class="flex space-x-2">
			<div class="flex">
				<a class="text-slate-500 hover:text-slate-700" href="#">
					<svg xmlns="http://www.w3.org/2000/svg" width="30" height="30" fill="currentColor" class="bi bi-github" viewBox="0 0 16 16">
						<path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.012 8.012 0 0 0 16 8c0-4.42-3.58-8-8-8z"/>
					</svg>
				</a>
			</div>
		</div>
	</nav>
	<div class="flex justify-center px-4">
		<div class="flex flex-col max-w-2xl">
			<div class="flex my-20 justify-center">
				<div class="flex flex-col space-y-2 text-center">
					<p class="font-semibold text-4xl md:text-5xl mb-1">
						Fedora Post-Install
					</p>
					<p class="text-2xl text-gray-500">
						The ultimate post-installation guide for Fedora Linux.
					</p>
				</div>
			</div>
			<div class="flex flex-col">
				<Title text="Base configuration"></Title>
				<Subtitle text="1. Update the system" />
					<Paragraph>
						We can update Fedora after installing it one of two ways, the first one is 	
						using the graphical interface and the second via the terminal.
					</Paragraph>
					<ParagraphItalic>
						If you want update your system using the graphical interface:
					</ParagraphItalic>
					<ParagraphItalic>
						If you want to update your system using the terminal:
					</ParagraphItalic>
					<Paragraph>
						Press the home button followed by the word <span class="underline">terminal</span> 
						and press Enter. A new terminal will open. Type the following command to update your system:
					</Paragraph>
					<CodeSnippet>
						sudo dnf upgrade
					</CodeSnippet>
					<Paragraph>
						Remember to type 'y' when prompted for a confirmation to proceed with the installation.
					</Paragraph>
				<Subtitle text="2. Install RPM Fusion" />
					<Paragraph>
						Fedora can't ship many packages that considerable improve your experience because of the legal 
						reasons that Red Hat (the company which sponsorships Fedora) is bound by. To learn more about this 
						topic you can refer to <Redirect link="https://docs.fedoraproject.org/en-US/legal/">Fedora's Legal Resources</Redirect>.
					</Paragraph>
					<Paragraph>
						RPM Fusion, as stated in their <Redirect link="https://rpmfusion.org/">website</Redirect>, “provides 	
						software that the Fedora Project or Red Hat doesn't want to ship. That software is provided as precompiled RPMs 	
						for all current Fedora versions and current Red Hat Enterprise Linux or clones versions.”
					</Paragraph>
					<Paragraph>
						They're two different software repositories which you can enable: free and non-free. For more information consult 	
						the RPM Fusion following <Redirect link="https://rpmfusion.org/Configuration">page</Redirect>. We recommend installing 	
						both of them. To do this, open the terminal and run the following command:
					</Paragraph>
					<CodeSnippet>
						sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
					</CodeSnippet>
				<Subtitle text="3. Install Additional Plugins" />
					<Paragraph>
						As for now, you still can't play various types of video and audio types in your system. To do so, you need to install the 	
						following packages that provide multimedia plugins:
					</Paragraph>
					<ParagraphItalic>
						Note: this step requires the installation of RPM Fusion.
					</ParagraphItalic>
					<CodeSnippet>
						sudo dnf install gstreamer1-plugins-{'{'}bad-\*,good-\*,base{'}'} gstreamer1-plugin-openh264 gstreamer1-libav --exclude=gstreamer1-plugins-bad-free-devel
sudo dnf install lame\* --exclude=lame-devel
sudo dnf group upgrade --with-optional Multimedia
					</CodeSnippet>
					<Paragraph>
						For more information visit this <Redirect link="https://docs.fedoraproject.org/en-US/quick-docs/assembly_installing-plugins-for-playing-movies-and-music/">page</Redirect> 
						from the fedora docs.
					</Paragraph>
					<Paragraph>
						You can additionally install media players that include some of video and audio codecs by themselves. Some of the most popular players include 	
						<Redirect link="https://www.videolan.org/vlc/">vlc</Redirect> and <Redirect link="https://mpv.io/">mpv</Redirect>.
					</Paragraph>
					<Paragraph>
						If you wish to install the vlc media player (Recommended), you can do so with the following command:
					</Paragraph>
					<CodeSnippet>
						sudo dnf install vlc
					</CodeSnippet>
					<Image img_src={random_doggo} />
			</div>
		</div>
	</div>
</div>
