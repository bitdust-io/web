<template>
    <i class="file-extension"
       v-bind:style="{ 'background': 'url(' + getExtension() + ')' }">
    </i>

</template>

<script>
    const iconList = ['aac', ' ai', 'aiff', 'avi', 'c', 'cpp', 'css', 'csv', 'dat', 'dmg', 'doc', 'exe', 'flv', 'gif', 'h', 'hpp', 'html', 'ics', 'java', 'jpg', 'js', 'key', 'mid', 'mp3', 'mp4', 'mpg', 'pdf', 'php', 'png', 'ppt', 'psd', ' py', 'q', 't', 'rar', 'rb', 'rtf', 'sql', 'tiff', 'txt', 'wav', 'xls', 'xml', 'yml', 'zip'];

    export default {
        name: 'fileExtension',
        data() {
            return {};
        },
        props: ['file'],
        methods: {
            getExtension() {
                if (!this.file) return;
                return this.makeUrl(this.file.toLowerCase().match(/[^.]+$/)[0]);
            },
            makeUrl(extension) {
                if (iconList.indexOf(extension) === -1) {
                    return process.env.BASE_URL + 'extensions/icon-file-gray.svg';
                }
                return process.env.BASE_URL + 'extensions/' + extension + '.png';
            }
        }
    };
</script>

<style scoped lang="scss">
    i {
        width: 20px;
        height: 20px;
        display: inline-block;
        margin-right: 10px;
        background-size: 90% !important;
        background-repeat: no-repeat !important;
    }
</style>
