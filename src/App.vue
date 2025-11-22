<script setup>
    import { ref } from 'vue'
    import Link from '@/components/Link.vue'

    const downloadToFile = (content, filename, contentType) => {
        const a = document.createElement('a')
        const file = new Blob([content], { type: contentType })

        a.href = URL.createObjectURL(file)
        a.download = filename
        a.click()

        URL.revokeObjectURL(a.href)
    }
    const onVcardClick = (e) => {
        const vcard = `
        BEGIN:VCARD
        VERSION:3.0
        FN;CHARSET=UTF-8:Tierry Danquin
        N;CHARSET=UTF-8:Danquin;Tierry;;;
        GENDER:M
        EMAIL;CHARSET=UTF-8;type=HOME,INTERNET:contact@oothkoo.com
        TEL;TYPE=WORK,VOICE:0658274556
        ADR;CHARSET=UTF-8;TYPE=HOME:;;;Paris;;;France
        URL;CHARSET=UTF-8:http://oothkoo.com
        X-SOCIALPROFILE;TYPE=twitter:https://twitter.com/oothkoo
        X-SOCIALPROFILE;TYPE=linkedin:https://www.linkedin.com/in/tierry-danquin-oothkoo
        X-SOCIALPROFILE;TYPE=CV:https://www.oothkoo.com/wp-downloads/cv-tierry-danquin.pdf
        REV:2025-11-21T09:35:17.928Z
        END:VCARD`

        downloadToFile(vcard, 'tierry-danquin.vcf', 'text/vcard')
    }

    const showQRcodeDialog = ref(false)
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
        },
        {
            icon: 'fa-solid fa-qrcode',
            text: 'QR Code',
            url: '#',
            click: () => {
                showQRcodeDialog.value = true
            }
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
            <div
                class="save-btn"
                @click="onVcardClick"
            >Save Contact</div>
        </div>
    </div>

    <VaModal
        class="qrcode-dialog"
        v-model="showQRcodeDialog"
        hide-default-actions
        close-button
        max-width="350px"
    >
        <img class="qrcode" src="/assets/qrcode.svg" border="0" />

        <VaButton
            class="download-qrcode-btn"
            icon="download"
            href="/assets/qrcode.svg"
            target="_blank"
        >
            Download
        </VaButton>
    </VaModal>
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
    .qrcode-dialog {
        
        .va-modal__message {
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
        }

        .qrcode {
            max-width: 300px;
        }
        .download-qrcode-btn {
            margin-top: 10px;
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
            background: white;

            @media (min-width: 768px) {
                max-width: 440px;
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
                        width: 100%;
                        
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
                    color: white;
                    
                    box-shadow: 0 1px 5px 0 rgb(82 93 102 / 25%), 0 2px 8px 0 rgb(82 93 102 / 15%);
                    cursor: pointer;
                }
            }
        }
    }
</style>
