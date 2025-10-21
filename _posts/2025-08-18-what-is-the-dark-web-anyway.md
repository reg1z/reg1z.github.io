---
layout: post
title: "What IS the Dark Web Anyway?"
date: 2025-08-18
last-updated: 2025-08-18
categories:
toc:
image:
  path: https://raw.githubusercontent.com/reg1z/pics/refs/heads/main/shiningLight.webp
  alt:
description:
---
{% include embed/youtube.html id="68Ia5TBI6pI" %}

What imagery does the phrase "Dark Web" evoke in your mind?

To most, the Dark Web is an urban legend. It's likened to a monster hiding under the bed—a space normally safe, purposeful, and necessary turned enigmatic, ominous, and sinister. Where an accidental dangling of a foot off the mattress could end in tragedy.

In the last twenty years, the term has become a catch-all scapegoat that people point to whenever hidden, illicit activities are uncovered online and thrust into the limelight. I'd like to demystify that notion. Would you be surprised to learn that crime is a far cry from the original intent behind the technologies making up most of the Dark Web?

What if this shadowy back alley is one of the last places you can walk unseen? One of the few online spaces where a semblance of privacy, anonymity, and freedom of speech persist?

This is the first in a series of articles to be published on the Dark Web, Darknets, and enhancing one's privacy online.

![](https://raw.githubusercontent.com/reg1z/pics/refs/heads/main/darkweb1.webp)

## Legitimate Uses of the Dark Web

From a cultural perspective, the Dark Web isn't often associated with lawful activities. And for good reason. There are numerous cases of prominent crime occurring on the Dark Web.

Despite that, Darknets (and the Dark Web as a whole) remain useful tools for many legitimate purposes. In the case of Tor, it was built not as a tool to facilitate crime, but for the prevention of surveillance and tracking. You can see the Tor Project's history page for more details.

The Dark Web can be used for...

- Privacy. One's ability to control access to their personal data. The Dark Web is powerful when applied as a personal privacy control, especially in authoritarian contexts.
- Anonymity. A distinct concept often conflated with privacy. The freedom for one to act without their actions being linked to their own identity.
- As close to a guarantee of freedom of speech as one can get online. When the confidentiality and integrity of data has been built into the network protocol itself, one is empowered to communicate their thoughts freely... as long as they've taken necessary precautions and considered all facets of their unique security context (more on this later).
  - Conversely, this can also facilitate the spread of misinformation and disinformation. Always question every source you find. Maintain your media literacy.
    - Censorship circumvention.
    - Protection of dissidents from political reprisal.
    - Whistle-blowing.
    - Marketplaces and other anonymized or privacy-oriented service providers.
    - Open Source Intelligence (OSINT). The Dark Web is a source not always considered when performing web recon. Depending on the target, it just might be a valuable source of information. It can also aid a researcher in anonymizing communications that might otherwise reach the target. Do not do this without first assessing risks posed to you. This is not an endorsement or guide.

> Please note that Infophreak does not encourage or endorse these actions. This article is not a guide or "how-to" for these particular activities; it simply aims to communicate the legitimate, ethical use of the Dark Web as a resource.

## The Surface Web, and What Lies Under

When one considers accessing the Dark Web, the first thought usually involves using the Tor Browser. Tor has become virtually synonymous with the Dark Web, when in fact, the Tor network is only one subset of it. It is a single "Darknet" used to anonymize internet traffic.

But what is a Darknet? Before we continue, it's important to clarify some key terms. There is a lot of conceptual overlap in the knowledge required to understand Darknets. So, we need to be specific and consistent about definitions when covering them.

Here are the basic elements we can use to understand the context the Dark Web rests within:

- World Wide Web: The internet as accessed through a web browser.
- Surface Web: Portion of the World Wide Web that IS indexed (or CAN BE indexed) by standard search engines. These parts of the web are the easiest to access, hosting popular services omnipresent in everyday internet use.
- Deep Web: Portion of the World Wide Web NOT indexed by standard search engines. This is a purposefully broad category, referring to literally ANY non-indexed content hosted on the Web. Consists of things like backend dashboards, databases, and generally any "private" page that is otherwise inaccessible, whether intentionally or not.
- Dark Web: Portions of the World Wide Web hosted on individual Darknets.

Because the Dark Web is not index-able by standard search engines, it can be considered to exist nested within the Deep Web:

![](https://raw.githubusercontent.com/reg1z/pics/refs/heads/main/DarkwebIceberg.webp)

## Darknets: Building Blocks of the Dark Web

Now that we've covered some fundamentals, we can finally answer our earlier question: "...what is a Darknet?" Let's dive into Clearnets and Darknets, two major categories of networks often used to differentiate the Dark Web from the rest of the Internet.

### Clearnets

Clearnets (not to be confused with Cleartext) comprise the default "layer" of the Web most are accustomed to. Communications on Clearnet networks are usually not anonymous or privacy-friendly. Most sites "fingerprint" users through various metrics such as one's IP address, screen size, and more. A Clearnet can be thought of as polar opposite to a Darknet. Essentially, the Surface Web is thought to be composed of Clearnets—the Surface Web can also be considered a very large Clearnet in and of itself.

### Darknets

A Darknet is an overlay network that operates within the Internet. These overlay networks are implemented as additional layers ON TOP of existing communication protocols, providing anonymity and privacy—and therefore plausible deniability—to users. They can be considered a "mask" that obfuscates or outright eliminates information that can be associated with the user. In many cases, they operate on existing network segments that would otherwise be considered part of a Clearnet.

The degree of "guaranteed" anonymity and privacy varies depending on how an individual Darknet's protocols and software have been designed—a process typically informed by a Threat Model for the overall project. Darknets can be considered as distinct from one another by assessing the key differences in their protocols, software, and the Threat Models informing their design. They are most often developed as open-source collaborative community projects, as is the case with the Tor Project.

To access a specific Darknet, one must obtain specific software tailored for it. Again, the Tor Browser is the perfect example. Tor uses a protocol known as Onion Routing (TOR stands for "The Onion Router") to provide anonymity and privacy. To access the Tor Darknet, one MUST use the Tor Browser or some other form of purpose-built software that implements its protocol.

I will not go into extensive detail on any particular Darknet in this article, but it's important to note that (normally) for a Darknet to adequately function, a significant amount of user buy-in may be required. Tor works by routing traffic through a randomized sequence of relays. On the Tor Project's website, you can actually view their public metrics on the number of relays currently operating across the globe.

But who hosts these relays? Ideally, it would be someone passionate about the project, who bears no ill intentions and does it for the satisfaction of providing the service alone. However, this isn't always the case. Many different parties are known to host Tor relays, and it's impossible to know their true motivations. Considering the method by which a Darknet's infrastructure is implemented is INTEGRAL in assessing its compatibility with one's own Threat Model. Some Darknets exist for the "ultra-paranoid," while others can be considered "safe enough" for most people.

A non-exhaustive list of notable Darknets includes:

- Tor
- I2P
- Hyphanet
- GNUnet

Note that many other Darknet projects exist, but because of the broad range of user-bases, lesser-known projects have varying levels of community support. Many have also been left abandoned or otherwise deprecated.

## Bringing it All Together

Bringing it All Together

From a bird's eye view, this is the essence of the Dark Web. It's simply a grouping of individual Darknets that are actually completely segmented from one another. That being said, there are circumstances where intercommunication between two Darknets (or a tunnel through multiple Darknets) is desirable. Just because they exist as distinct networks doesn't make their interplay impossible. Alas, that is out-of-scope for this post.

This was the first in a series of articles to be published on the Dark Web, Darknets, and enhancing your privacy online.

I am grateful for your readership. Be sure to stay tuned for further entries where I'll dive deeper into the machinations of the DARK WEB.

## Sources

- The Tor Project: https://www.torproject.org/
- Tor Browser User Manual: https://tb-manual.torproject.org/
- The Tor Project's Official GitLab code repository: https://gitlab.torproject.org/tpo
- Whonix Documentation: https://www.whonix.org/wiki/Documentation
- The Invisible Internet Project (I2P): https://geti2p.net/en/
- Hyphanet: https://www.hyphanet.org/index.html
- GNUnet: https://www.gnunet.org/en/index.html
-The First Amendment: https://constitution.congress.gov/constitution/amendment-1/
- PrivacyGuides Knowledge Base on Threat Modeling: https://www.privacyguides.org/en/basics/threat-modeling/
