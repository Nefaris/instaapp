<template>
    <div class="postcard">
        <div class="topBar">
            <div class="userDatails">
                <img class="userIcon" src="../assets/user-solid.svg" alt=""/>
                <p class="username">{{ username }}</p>
            </div>
        </div>
        <img class="photo" :src="imageSrc" alt="">
        <div class="contentContainer">
            <div class="actionsBar">
                <div class="views">
                    <img class="viewsIcon" src="../assets/eye-solid.svg" alt=""/>
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
    export default {
        name: "Postcard",
        props: {
            imageSrc: String,
            imageDesc: String,
            viewsCount: Number,
            username: String
        }
    }
</script>

<style scoped lang="scss">
    .postcard {
        border-top: 1px solid rgba(0, 0, 0, .0975);
        border-bottom: 1px solid rgba(0, 0, 0, .0975);
        margin-bottom: 60px;

        @media(min-width: 600px) {
            border-left: 1px solid rgba(0, 0, 0, .0975);
            border-right: 1px solid rgba(0, 0, 0, .0975);
            background-color: #ffffff;
        }
    }

    .contentContainer {
        padding: 12px 20px;
    }

    .userDatails {
        display: flex;
        align-items: center;
    }

    .username {
        margin: 0;
        font-weight: bold;
        font-size: 14px;
    }

    .userIcon {
        max-width: 18px;
        margin-right: 14px;
    }

    .topBar {
        padding: 20px 20px;
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