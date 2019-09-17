<template>
    <div class="postcard">
        <div class="topBar">
            <div class="userDatails">
                <img class="userIcon" src="../assets/img/user-solid.svg" alt=""/>
                <p class="username">{{ username }}</p>
            </div>
            <div class="dateDetails">
                {{ postDate }}
            </div>
        </div>

        <img v-if="imageSrc.length === 1" class="photo" :src="imageSrc" alt="">
        <Carousel v-if="imageSrc.length > 1" :images-array="imageSrc"/>

        <div class="contentContainer">
            <div class="actionsBar">
                <div class="views">
                    <img class="viewsIcon" src="../assets/img/eye-solid.svg" alt=""/>
                    <p class="viewsCount">
                        {{ viewsCount }}
                    </p>
                </div>
            </div>
            <div class="description">
                <p>{{ imageDesc }}</p>
            </div>
        </div>
    </div>
</template>

<script>
    import Carousel from "./Carousel";

    export default {
        name: "Postcard",
        components: {
            Carousel
        },
        props: {
            imageSrc: Array,
            imageDesc: String,
            viewsCount: Number,
            username: String,
            postDate: String
        }
    }
</script>

<style scoped lang="scss">
    @import "../assets/scss/theme";

    $postCardVerticalSpace: 20px;

    .postcard {
        border-top: $postCardBorderColor;
        border-bottom: $postCardBorderColor;
        margin-bottom: 60px;

        @media(min-width: 600px) {
            border-left: $postCardBorderColor;
            border-right: $postCardBorderColor;
            background-color: $backgroundWhite;
            box-shadow: 0 0 5px 0 rgba(0, 0, 0, .05), 0 2px 10px 0 rgba(0, 0, 0, .05);
        }
    }

    .contentContainer {
        padding: 12px $postCardVerticalSpace;
    }

    .userDatails {
        display: flex;
        flex-grow: 1;
        align-items: center;
    }

    .dateDetails {
        font-size: 14px;
        font-weight: bold;
    }

    .username {
        margin: 0;
        font-weight: bold;
        font-size: 14px;
    }

    .userIcon {
        max-width: 18px;
        margin-right: 14px;
        margin-top: -2px;
    }

    .topBar {
        padding: 20px $postCardVerticalSpace;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .photo {
        max-width: 100%;
    }

    .actionsBar {
        margin-top: 10px;
    }

    .views {
        display: flex;
        align-items: center;
    }

    .viewsIcon {
        max-width: 20px;
        margin-right: 6px;
        padding-bottom: 1px;
    }

    .viewsCount {
        margin: 0;
        color: #000000;
        font-weight: bold;
        font-size: 14px;
    }

    .description {
        padding: 10px 0;

        p {
            margin: 0;
            color: #000000;
            font-size: 14px;
            line-height: 1.5;
            text-align: left;
        }
    }
</style>