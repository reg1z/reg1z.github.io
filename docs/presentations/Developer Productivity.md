## Developer Productivity

*(What's a better term for the title here? Computer productivity? Sounds too generic)*
- "Productivity" might not be the best / healthiest way to present it
#### Considerations
- **Why would you want to *implement* this stuff?:**
	- It can be fun.
		- Learning keybindings. Lots of games for this kind of stuff online. Typeracer, vimracer, etc.
		- Configuring your own environment
		- Theming/ricing (less practical, but makes ya feel good)
	- Customizable
	- Can leave an impression.
		- It can be impressive. Its how to become like the stereotypical hacker archetype. Or at least it makes you *look* like it to people that don't know what's going on.
		- Can be used to show a certain "*seriousness*" or "*care*" (for lack of a better term) for your discipline, if applicable.
			- Don't get all obnoxious or elitist about it, though. Existing accessible tools + user-friendliness ARE NOT things you should denigrate or want to take an stance against.
	- It's a hobby.
- **Potential Caveats**
	- Security
		- custom individualized configurations can be used to fingerprint you. If your personal configs/dotfiles are publicly available somewhere and your host is then compromised... the matching configs from the repo + your system could be used to identify you. This might not be a big deal.
	- Learning curve
	- Config management can be a headache
- ⭐ You don't need to adopt ALL lessons here. The techniques presented have *individual* merits. There are too many tools/approaches to go over in a single session. Just note that you DO NOT have to treat what's presented as a monolith. You can pick, choose, and experiment to find out what works for you.

### Adjacent pathways
- **Alternate keyboard layouts**. These can be compelling and can help you out in many ways, but there are a LOT of cons. Generally has a much higher skill floor than other options for much less reward. Most people will always use QWERTY, and 95% of software is and is likely *to be* designed for it.

### Tiling Window Managers

Potential Benefits:
- You might free up mental energy lost when managing your own desktop environment windows or losing track of thing.
	- That being said it takes practice to get to that point. BUT, depending on practice, you might see positive results in as little as a couple days to a week.
- Speed. automatic management of windows/interfaces.

The Software:
- Windows → **GlazeWM** https://github.com/glzr-io/glazewm
	- Glaze is inspired by **i3**.
	- There are few other reasonable options. Glaze just got a shiny new Rust re-design and has the most backing behind it. 
- Linux → MANY options, but the most popular is **i3** https://i3wm.org/
	- If you're wanting to use a Wayland-based environment (not X11), there are many options:
		- **sway** is the wayland counterpart of i3, and largely compatible with most i3 configurations https://swaywm.org/
		- **Hyprland** is the best tiling WM (*in my opinion*) in terms of both form AND functionality. BUT, I don't recommend it for anyone's first tiling WM experience unless using a distro-default config, etc. It is still in beta. It has support for some intuitive layout configs that allow for functionality you would only find in specific tiling WMs (bspwm, etc). It's also very pretty out of the box. Has phenomal documentation, support, and a community surrounding it. It is still a WIP (as is the Wayland protocol). It is still finicky for many people. Keep in mind it is currently difficult to test hyprland in a VM environment. https://hyprland.org/
		- The Linux community is moving toward Wayland! X11 remains the most stable option, especially on older hardware (10-15 year old+ *circa 2025*).
- Mac
	- ???

Potential examples of cool things
- accessible "drop-in" for VMs/chatgpt/etc

### Terminal / console efficiency
might be an element of the developer productivity series
- wezterm (cross-platform config w/ lua)
	- Allows for multiplexing 
- tmux + the idea of multiplexers
	- if you have access to tmux on a remote host, it makes things so much simpler when all you have is access to a shell via ssh
- 

### vi and vim/nvim Motions
Oh man...
- Makes editing text so much better. But can feel as if you're learning the piano at the start.
- practice in software you already use
	- vscode / browser
- vimracer


### Configuration Management | Managing your Dotfiles
- There are tools that you will be / have been taught that are very useful in keeping your configuration sync'd...
- **GNU Stow** https://www.gnu.org/software/stow/
- **Ansible** https://github.com/ansible/ansible
	- An IaC tool, but great for personal configuration setup and secrets management.
	- You might end up having to learn ansible at a future job as well. It's a good skill to have on the resume.
- Setting up an accessible repo...