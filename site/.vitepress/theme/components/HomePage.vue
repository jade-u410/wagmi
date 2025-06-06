<script setup lang="ts">
import type DefaultTheme from 'vitepress/theme'
import { VPButton, VPSponsors, VPTeamMembers } from 'vitepress/theme'
import { farcasterIcon } from '../../constants'
import { useSponsors } from '../composables/useSponsors'

const { data: sponsors } = useSponsors()

const teamMembers = [
  {
    avatar: 'https://www.github.com/tmm.png',
    name: 'tmm',
    links: [
      { icon: 'github', link: 'https://github.com/tmm' },
      { icon: 'bluesky', link: 'https://bsky.app/profile/tmm.dev' },
      { icon: 'x', link: 'https://twitter.com/awkweb' },
      {
        icon: {
          svg: farcasterIcon,
        },
        link: 'https://warpcast.com/awkweb',
      },
    ],
  },
  {
    avatar: 'https://www.github.com/jxom.png',
    name: 'jxom',
    links: [
      { icon: 'github', link: 'https://github.com/jxom' },
      { icon: 'bluesky', link: 'https://bsky.app/profile/jxom.dev' },
      { icon: 'x', link: 'https://twitter.com/_jxom' },
      {
        icon: {
          svg: farcasterIcon,
        },
        link: 'https://warpcast.com/jxom',
      },
    ],
  },
] satisfies DefaultTheme.TeamMember[]
</script>

<template>
  <div class="content">
    <div class="content-container">
      <main class="main">
        <div class="vp-doc" flex flex-col items-center mt-10>
          <h2 id="meet-the-team" op50 font-normal p="t-10 b-2">
            Meet The Team
          </h2>
          <div w-full p-10>
            <VPTeamMembers size="small" :members="teamMembers" />
          </div>

          <h2 id="sponsored-by" op50 font-normal pt-5 pb-2>
            Sponsored by
          </h2>

          <div w-full p-10 class="container">
            <VPSponsors v-if="sponsors" :data="sponsors" />

            <div pt-10 text-center>
              <VPButton theme="alt" text="Become a sponsor" href="https://github.com/sponsors/wevm" />
            </div>
          </div>

          <div flex flex-col gap-2 items-center pt-10>
            <div>
              <a href="https://vercel.com/?utm_source=wevm&utm_campaign=oss">
                <img src="https://www.datocms-assets.com/31049/1618983297-powered-by-vercel.svg" alt="Powered by Vercel" h8>
              </a>
            </div>
            <div>
              <a href="https://quicknode.com/?utm_source=wevm&utm_campaign=oss">
                <img src="https://raw.githubusercontent.com/wevm/.github/refs/heads/main/content/quicknode-badge.svg" alt="Powered by QuickNode" h8>
              </a>
            </div>
          </div>
        </div>
      </main>
    </div>
  </div>
</template>

<style>
.vp-doc .VPTeamMembers.small.count-2 .container {
  max-width: calc(276px * 2 + 24px) !important;
}

.container {
  margin: 0 auto;
  max-width: 1152px;
}

h3.vp-sponsor-tier {
  margin: 0;
  margin-bottom: 4px;
}

.VercelBadge {
  align-items: center;
  color: var(--vp-c-text-2) !important;
  display: flex;
  font-size: 0.85rem;
  font-weight: 500;
  gap: 0.35rem;
  justify-content: center;
}

.VercelBadge:hover {
  text-decoration: none !important;
}

.VercelBadge svg {
  color: var(--vp-c-text-2);
  height: 0.85rem;
}
</style>
