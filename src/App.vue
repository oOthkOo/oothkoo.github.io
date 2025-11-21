<script setup>
    import { ref } from 'vue'
    import Link from '@/components/Link.vue'

    const links = ref([
        {
            icon: 'fa-solid fa-envelope',
            text: 'contact@oothkoo.com',
            url: 'mailto:contact@oothkoo.com'
        },
        {
            icon: 'fa-solid fa-phone',
            text: '0658274556',
            url: 'tel:0658274556'
        },
        {
            icon: 'fa-solid fa-file-pdf',
            text: 'Resume (CV)',
            url: 'https://www.oothkoo.com/wp-downloads/cv-tierry-danquin.pdf'
        },
        {
            icon: 'fa-brands fa-linkedin',
            text: 'oothkoo',
            url: 'https://www.linkedin.com/in/tierry-danquin-oothkoo'
        },
        {
            icon: 'fa-brands fa-github',
            text: 'oothkoo',
            url: 'https://github.com/oothkoo'
        },
        {
            icon: 'fa-brands fa-x-twitter',
            text: 'oothkoo',
            url: 'https://twitter.com/oothkoo'
        },
        {
            icon: 'fa-regular fa-window-maximize',
            text: 'oothkoo.com',
            url: 'http://oothkoo.com'
        }
    ])
</script>

<template>
    <div class="home">
        <div class="header">
            <div class="banner">
                <img class="image" src="/assets/banner.avif" border="0" />
            </div>
            <div class="avatar">
                <img class="image" src="/assets/avatar.avif" border="0" />
            </div>
        </div>
        <div class="resume">
            <div class="name">Tierry Danquin</div>
            <div class="role">Developer</div>
        </div>
        <div class="links">
            <Link
                v-for="link in links"
                :link="link"
            />
        </div>
        <div class="footer">
            <a
                class="link"
                href="vcard;base64,QkVHSU46VkNBUkQKVkVSU0lPTjozLjAKRk47Q0hBUlNFVD1VVEYtODpUaWVycnkgRGFucXVpbgpOO0NIQVJTRVQ9VVRGLTg6RGFucXVpbjtUaWVycnk7OzsKR0VOREVSOk0KRU1BSUw7Q0hBUlNFVD1VVEYtODt0eXBlPUhPTUUsSU5URVJORVQ6Y29udGFjdEBvb3Roa29vLmNvbQpURUw7VFlQRT1XT1JLLFZPSUNFOjA2NTgyNzQ1NTYKQURSO0NIQVJTRVQ9VVRGLTg7VFlQRT1IT01FOjs7O1BhcmlzOzs7RnJhbmNlClVSTDtDSEFSU0VUPVVURi04Omh0dHA6Ly9vb3Roa29vLmNvbQpYLVNPQ0lBTFBST0ZJTEU7VFlQRT10d2l0dGVyOmh0dHBzOi8vdHdpdHRlci5jb20vb290aGtvbwpYLVNPQ0lBTFBST0ZJTEU7VFlQRT1saW5rZWRpbjpodHRwczovL3d3dy5saW5rZWRpbi5jb20vaW4vdGllcnJ5LWRhbnF1aW4tb290aGtvbwpYLVNPQ0lBTFBST0ZJTEU7VFlQRT1DVjpodHRwczovL3d3dy5vb3Roa29vLmNvbS93cC1kb3dubG9hZHMvY3YtdGllcnJ5LWRhbnF1aW4ucGRmClJFVjoyMDI1LTExLTIxVDA5OjM1OjE3LjkyOFoKRU5EOlZDQVJE=="
                download="tierry-danquin.vcf"
            >
                <div class="save-btn">Save Contact</div>
            </a>
        </div>
    </div>
</template>

<style>
    html {
        @media (min-width: 768px) {
            height: 100%;
        }
    }
    body {
        font-family: Ubuntu;
        color: #2b2b2b;
        margin: 0;

        @media (min-width: 768px) {
            height: 100%;
        }
    }
    #app {
        @media (min-width: 768px) {
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 22px;
            padding: 30px 0px 30px 0px;
            background: rgba(53,57,59, .14);
        }

        .home {
            max-width: 440px;
            background: white;

            @media (min-width: 768px) {
                border-radius: 22px;
                box-shadow: 0 0 0 1px rgba(15, 15, 15, .05), 0 3px 6px rgba(15, 15, 15, .1), 0 9px 24px rgba(15, 15, 15, .2);
            }

            .header {
                height: 307px;

                @media (min-width: 768px) {
                    border-radius: 22px 22px 0px 0px;
                }

                .banner {

                    .image {
                        
                        @media (min-width: 768px) {
                            border-radius: 22px 22px 0px 0px;
                        }
                    }
                }
                .avatar {
                    width: 120px;
                    margin-left: 1.5rem;
                    position: relative;
                    bottom: 60px;
                    border-radius: 50%;
                    box-shadow: 0 2px 4px 0 rgba(22,29,37,.1),0 0 0 3px #fff;

                    .image {
                        width: 120px;
                        height: 120px;
                        border-radius: 50%;
                    }
                }
            }
            .resume {
                margin: 1.5rem;
                overflow-wrap: break-word;

                .name {
                    margin-bottom: 0.5rem;
                    font-size: 2rem;
                    font-weight: 600;
                    line-height: 1.3;
                }
                .role {
                    font-size: 1.5rem;
                    font-weight: 500;
                    line-height: 1.2;
                    color: #35393b;
                }
            }
            .links {

            }
            .footer {
                display: flex;
                align-items: center;
                justify-content: center;
                margin-top: 1.25rem;
                padding: 1.5rem 2rem 1.75rem;
                position: sticky;
                bottom: 0;
                background: linear-gradient(180deg,rgba(255,255,255,0),rgba(255,255,255,.9) 40%);

                @media (min-width: 768px) {
                    border-radius: 0px 0px 22px 22px;
                }

                .link {
                    text-decoration: none;
                    color: white;

                    .save-btn {
                        max-width: 220px;
                        padding: .75rem 2.5rem;
                        border-radius: 80px;
                        white-space: nowrap;
                        font-weight: 700;
                        font-size: 1.375rem;
                        text-align: center;
                        letter-spacing: .3px;
                        background: #2b2b2b;
                        
                        box-shadow: 0 1px 5px 0 rgb(82 93 102 / 25%), 0 2px 8px 0 rgb(82 93 102 / 15%);
                        cursor: pointer;
                    }
                }
            }
        }
    }
</style>
