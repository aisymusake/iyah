<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>iMessage – Messages &amp; Chat</title>
<style>
  @import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&display=swap");

  :root {
    /* Colors */
    --color-black: #000000;
    --color-white: #ffffff;
    --color-grey: #909093;
    --color-blue: #3478f6;
    --color-avatar-bg: #e9e9ea;
    --color-lavender: #ddd3fb;
    --color-nav-bg: #f1f1f2;
    --color-nav-border: #b2b2b2;
    --color-input-border: #c5c5c7;
    --color-search-bg: rgba(118, 118, 128, 0.12);
    --color-search-text: rgba(60, 60, 67, 0.6);
    --color-canvas: #e5e5e5;

    /* Shadows */
    --shadow-avatar: 0 5px 20px rgba(166, 166, 166, 0.3);
    --shadow-cover: 0 0 15px rgba(0, 0, 0, 0.1);

    /* Fonts */
    --font-inter: "Inter", -apple-system, "Helvetica Neue", Arial, sans-serif;
    --font-sf-text: "SF Pro", "SF Pro Text", -apple-system, "Inter", sans-serif;
    --font-sf-compact: "SF Compact Display", "SF Pro Text", -apple-system, "Inter", sans-serif;
    --font-sf-display: "SF UI Display", "SF Pro Display", -apple-system, "Inter", sans-serif;

    /* Font sizes */
    --fs-10: 10px;
    --fs-12: 12px;
    --fs-13: 13px;
    --fs-14: 14px;
    --fs-15: 15px;
    --fs-17: 17px;
    --fs-17-67: 17.67px;
    --fs-18: 18px;
    --fs-36: 36px;

    /* Spacing */
    --space-2: 2px;
    --space-3: 3px;
    --space-5: 5px;
    --space-8: 8px;
    --space-12: 12px;
    --space-16: 16px;

    /* Radii */
    --radius-pill: 100px;

    /* Screen scale (responsive) */
    --screen-scale: 1;
  }

  *, *::before, *::after { box-sizing: border-box; }

  html, body { margin: 0; padding: 0; }

  body {
    background: var(--color-canvas);
    font-family: var(--font-inter);
    -webkit-font-smoothing: antialiased;
  }

  ul { list-style: none; margin: 0; padding: 0; }
  p, h1, h2 { margin: 0; }
  img { display: block; max-width: none; }
  button { font: inherit; background: none; border: 0; padding: 0; cursor: pointer; }

  .visually-hidden {
    position: absolute; width: 1px; height: 1px; overflow: hidden;
    clip: rect(0 0 0 0); white-space: nowrap;
  }

  /* ---------- Page layout ---------- */
  .stage {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: flex-start;
    gap: 40px;
    padding: 40px 20px;
  }

  .device {
    position: relative;
    flex: 0 0 auto;
    width: 402px;
    height: 874px;
    background: var(--color-white);
    overflow: hidden;
    zoom: var(--screen-scale);
  }

  /* ---------- Status bar (Messages screen) ---------- */
  .status-bar {
    position: absolute;
    left: 0; top: -3px;
    width: 402px; height: 62px;
    display: flex; align-items: center; justify-content: center;
    padding: 3px var(--space-8) 0;
    z-index: 5;
  }
  .status-bar__time {
    flex: 1 0 0; min-width: 1px; height: 13px;
    display: flex; align-items: center; justify-content: center;
  }
  .status-bar__time-text {
    font-family: var(--font-sf-text);
    font-weight: 590;
    font-size: var(--fs-17-67);
    line-height: 22px;
    color: var(--color-black);
    text-align: center;
    white-space: nowrap;
  }
  .status-bar__island-wrap { flex: 0 0 auto; padding-top: 0.167px; }
  .status-bar__island {
    width: 95px; height: 36.667px;
    background: var(--color-black);
    border-radius: var(--radius-pill);
  }
  .status-bar__levels {
    flex: 1 0 0; min-width: 1px;
    display: flex; align-items: center; justify-content: center;
    gap: var(--space-8);
  }
  .status-bar__cellular {
    display: flex; align-items: flex-end; gap: 2.333px; padding-top: 1.333px;
  }
  .status-bar__bar {
    width: 3.333px; background: var(--color-black); border-radius: 4px;
  }
  .status-bar__bar--1 { height: 6.333px; }
  .status-bar__bar--2 { height: 8.67px; }
  .status-bar__bar--3 { height: 11px; }
  .status-bar__bar--4 { height: 13.667px; }
  .status-bar__wifi { width: 19.333px; height: 14.333px; }
  .status-bar__battery { width: 29.333px; height: 13.667px; }

  /* ---------- Messages screen ---------- */
  .messages {
    position: absolute;
    left: 4px; top: 11px;
    width: 402px; height: 863px;
    background: var(--color-white);
    overflow: hidden;
  }

  /* Pins */
  .pin {
    position: absolute;
    display: flex; flex-direction: column; align-items: center;
    gap: var(--space-5);
  }
  .pin--col-1 { left: 22px; }
  .pin--col-2 { left: 149px; }
  .pin--col-3 { left: 276px; }
  .pin--row-1 { top: 148px; }
  .pin--row-2 { top: 282px; }
  .pin--row-3 { top: 416px; }
  .pin--group { overflow: hidden; }

  .pin__avatar {
    position: relative;
    flex-shrink: 0;
    width: 95px; height: 95px;
    border-radius: var(--radius-pill);
    box-shadow: var(--shadow-avatar);
  }
  .pin__avatar--group {
    box-shadow: none;
    background: var(--color-avatar-bg);
  }
  .pin__avatar--cover {
    background: var(--color-lavender);
    box-shadow: var(--shadow-cover);
  }
  .pin__emoji {
    position: absolute;
    left: 47px; top: 30px;
    transform: translateX(-50%);
    font-size: var(--fs-36);
    font-weight: 500;
    line-height: normal;
    color: var(--color-black);
    white-space: nowrap;
  }
  .pin__crop {
    position: absolute; inset: 0;
    overflow: hidden;
    border-radius: var(--radius-pill);
  }
  .pin__img {
    position: absolute; left: 0; top: 0;
    width: 100%; height: 100%;
  }
  .pin__img--cover {
    object-fit: cover;
    border-radius: var(--radius-pill);
  }
  .pin__img--aiz-1 { height: 116.84%; left: -9.93%; top: -5.26%; width: 119.87%; }
  .pin__img--aiz-3 { height: 386.97%; left: -38.89%; top: -69.47%; width: 178.8%; }
  .pin__img--atinn { height: 385.26%; left: -39.01%; top: -69.47%; width: 178.01%; }

  .pin__avatars { position: absolute; left: 9px; top: 12px; width: 78px; height: 75px; }
  .pin__ellipse { position: absolute; border-radius: 50%; }
  .pin__ellipse img {
    position: absolute; left: -15px; top: -15px;
    width: calc(100% + 30px); height: calc(100% + 30px);
  }
  .pin__ellipse--1 { left: 0; top: 0; width: 45px; height: 45px; }
  .pin__ellipse--2 { left: 43px; top: 26px; width: 35px; height: 35px; }
  .pin__ellipse--3 { left: 47px; top: 0; width: 23px; height: 23px; }
  .pin__ellipse--4 { left: 16px; top: 46px; width: 29px; height: 29px; }

  .pin__contact {
    display: flex; align-items: center; gap: var(--space-2);
    overflow: hidden;
  }
  .pin__badge { width: 10px; height: 10px; flex-shrink: 0; }
  .pin__name {
    font-family: var(--font-inter);
    font-weight: 500;
    font-size: var(--fs-13);
    line-height: 16px;
    color: var(--color-grey);
    text-align: center;
    white-space: nowrap;
  }

  /* Message list */
  .messages__list {
    position: absolute;
    left: 0; top: 548px;
    width: 375px;
    display: flex; flex-direction: column; gap: 1px;
    overflow: hidden;
  }
  .message {
    position: relative;
    flex-shrink: 0;
    width: 375px; height: 78px;
    background: var(--color-white);
  }
  .message--first { height: 77px; }
  .message__avatar {
    position: absolute; left: 26px; top: 15px;
    width: 45px; height: 45px;
    border-radius: var(--radius-pill);
  }
  .message__group {
    position: absolute; left: 26px; top: 15px;
    width: 45px; height: 45px;
    border-radius: var(--radius-pill);
    background: var(--color-avatar-bg);
  }
  .message__ellipse { position: absolute; border-radius: 50%; }
  .message__ellipse img {
    position: absolute; left: -15px; top: -15px;
    width: calc(100% + 30px); height: calc(100% + 30px);
  }
  .message__ellipse--1 { left: 4.26px; top: 5.68px; width: 21.316px; height: 21.316px; }
  .message__ellipse--2 { left: 24.63px; top: 18px; width: 16.579px; height: 16.579px; }
  .message__ellipse--3 { left: 26.53px; top: 5.68px; width: 10.895px; height: 10.895px; }
  .message__ellipse--4 { left: 11.84px; top: 27.47px; width: 13.737px; height: 13.737px; }

  .message__name {
    position: absolute; left: 83px; top: 9px;
    font-family: var(--font-inter);
    font-weight: 600;
    font-size: var(--fs-18);
    line-height: 1.21;
    color: var(--color-black);
    white-space: nowrap;
  }
  .message__text {
    position: absolute; left: 83px; right: var(--space-16); top: 31px;
    height: 36px;
    font-family: var(--font-inter);
    font-weight: 400;
    font-size: var(--fs-15);
    line-height: 1.21;
    color: var(--color-grey);
  }
  .message__time {
    position: absolute; right: var(--space-16); top: 10px;
    display: flex; align-items: center; gap: var(--space-5);
    overflow: hidden;
  }
  .message__time-text {
    font-family: var(--font-sf-compact);
    font-weight: 400;
    font-size: var(--fs-15);
    line-height: 18px;
    color: var(--color-grey);
    text-align: right;
    white-space: nowrap;
  }
  .message__chevron { position: relative; flex-shrink: 0; width: 16px; height: 16px; }
  .message__chevron img { position: absolute; inset: 0; width: 100%; height: 100%; }
  .message__chevron--partial img {
    inset: 12.5% 0 10.47% 54.93%;
    width: 45.07%; height: 77.03%;
  }
  .message__divider {
    position: absolute; left: 83px; top: 76.5px;
    width: 331px; height: 0.5px;
    background: var(--color-grey);
    opacity: 0.5;
  }

  /* Home indicator */
  .home-indicator {
    position: absolute;
    left: 22px; top: 810px;
    width: 375px; height: 34px;
  }
  .home-indicator::after {
    content: "";
    position: absolute;
    left: 50%; bottom: 8px;
    transform: translateX(-50%);
    width: 135px; height: 5px;
    background: var(--color-black);
    border-radius: var(--radius-pill);
  }

  /* Bubble */
  .bubble {
    position: absolute;
    left: 6px; top: 139px;
    width: 140px; height: 48px;
  }
  .bubble__shape {
    position: absolute; left: 0; top: 0;
    width: 140px; height: 47.9px;
  }
  .bubble__shape img {
    position: absolute; left: -15px; top: -15px;
    width: 170px; height: 77.9px;
  }
  .bubble__text {
    position: absolute; left: 70px; top: 21px;
    transform: translate(-50%, -50%);
    width: 126px; height: 42px;
    display: flex; align-items: center; justify-content: center;
    font-family: var(--font-inter);
    font-weight: 400;
    font-size: var(--fs-12);
    line-height: 1.25;
    color: var(--color-black);
    text-align: center;
    opacity: 0.9;
  }

  /* Reaction */
  .reaction {
    position: absolute;
    left: 338px; top: 412px;
    width: 29px; height: 33px;
  }
  .reaction img {
    position: absolute; left: -15px; top: -15px;
    width: 59px; height: 63px;
  }

  /* Search */
  .search {
    position: absolute;
    left: 2.01px; top: 90.53px;
    width: 402px; height: 38.26px;
    background: var(--color-white);
  }
  .search__field {
    position: absolute; left: -2px; right: -2px; bottom: 0;
    height: 36px;
  }
  .search__bg {
    position: absolute; left: 18px; right: 18px; top: 0;
    height: 36px;
    background: var(--color-search-bg);
    border-radius: 10px;
  }
  .search__input {
    position: absolute; left: 48px; right: 48px; top: 7px;
    height: 22px;
    padding: 0; border: 0; outline: 0;
    background: transparent;
    font-family: var(--font-inter);
    font-weight: 400;
    font-size: var(--fs-17);
    line-height: 22px;
    letter-spacing: -0.408px;
    color: var(--color-black);
    -webkit-appearance: none; appearance: none;
  }
  .search__input::placeholder { color: var(--color-search-text); opacity: 1; }

  /* Navigation bar */
  .nav {
    position: absolute;
    left: 17px; top: 41px;
    width: 375px; height: 44px;
    overflow: hidden;
  }
  .nav__title {
    position: absolute; left: 187.5px; top: 12px;
    transform: translateX(-50%);
    font-family: var(--font-sf-display);
    font-weight: 600;
    font-size: var(--fs-17);
    line-height: normal;
    color: var(--color-black);
    white-space: nowrap;
  }
  .nav__edit {
    position: absolute; left: 29px; top: 13px;
    transform: translateX(-50%);
    font-family: var(--font-sf-display);
    font-weight: 500;
    font-size: var(--fs-15);
    line-height: normal;
    color: var(--color-blue);
    white-space: nowrap;
  }

  /* ---------- Chat screen ---------- */
  .chat {
    position: absolute;
    left: 18px; top: 0;
    width: 389px; height: 874px;
    background: var(--color-white);
  }
  .chat__nav-shape {
    position: absolute;
    left: -18px; top: 1px;
    width: 407px; height: 116px;
    background: var(--color-nav-bg);
    box-shadow: 0 0.5px 0 0 var(--color-nav-border);
  }
  .chat__avatar {
    position: absolute; left: 164px; top: 45px;
    width: 48px; height: 48px;
    border-radius: var(--radius-pill);
    box-shadow: var(--shadow-avatar);
    overflow: hidden;
  }
  .chat__avatar img {
    position: absolute;
    height: 116.84%; left: -9.93%; top: -5.26%; width: 119.87%;
  }
  .chat__title {
    position: absolute; left: 165px; top: 95px;
    display: flex; align-items: center; gap: var(--space-3);
  }
  .chat__title-text {
    font-family: var(--font-inter);
    font-weight: 400;
    font-size: var(--fs-10);
    line-height: 15px;
    color: var(--color-black);
    text-align: center;
    white-space: pre;
  }
  .chat__chevron { width: 4px; height: 7px; transform: rotate(180deg); }
  .chat__back {
    position: absolute; left: 0; top: 49px;
    width: 40px; height: 40px;
  }
  .chat__back img, .chat__facetime img { width: 100%; height: 100%; }
  .chat__facetime {
    position: absolute; left: 331px; top: 56px;
    width: 26px; height: 26px;
  }

  .chat-status {
    position: absolute; left: 0; top: 0;
    width: 375px; height: 44px;
    overflow: hidden;
  }
  .chat-status__time {
    position: absolute; left: 18px; top: 12px;
    width: 54px; height: 21px;
    font-family: var(--font-sf-text);
    font-weight: 600;
    font-size: var(--fs-14);
    letter-spacing: -0.28px;
    line-height: 21px;
    color: var(--color-black);
    text-align: center;
  }
  .chat-status__battery { position: absolute; right: 15.67px; top: 17.33px; width: 24.328px; height: 11.333px; }
  .chat-status__wifi { position: absolute; inset: 39.39% 11.48% 35.69% 84.45%; }
  .chat-status__cellular { position: absolute; inset: 40.15% 16.62% 35.61% 78.84%; }
  .chat-status__wifi img, .chat-status__cellular img, .chat-status__battery img {
    position: absolute; inset: 0; width: 100%; height: 100%;
  }

  .chat__composer {
    position: absolute; left: 0; top: 778px;
    width: 375px; height: 48px;
    background: var(--color-white);
  }
  .chat__field {
    position: absolute; left: 58px; top: 6px;
    width: 302px; height: 36px;
    padding: 10px var(--space-12);
    border: 1px solid var(--color-input-border);
    border-radius: 80px;
    background: transparent;
    outline: 0;
    font-family: var(--font-sf-text);
    font-weight: 400;
    font-size: var(--fs-15);
    letter-spacing: -0.6px;
    color: var(--color-black);
    -webkit-appearance: none; appearance: none;
  }
  .chat__field::placeholder { color: var(--color-input-border); opacity: 1; }
  .chat__add {
    position: absolute; left: 12px; top: 7px;
    width: 34px; height: 34px;
  }
  .chat__add img { width: 100%; height: 100%; }
  .chat__home-indicator {
    position: absolute; left: 0; bottom: 17px;
    width: 375px; height: 34px;
  }
  .chat__home-indicator::after {
    content: "";
    position: absolute; left: 50%; bottom: 8px;
    transform: translateX(-50%);
    width: 135px; height: 5px;
    background: var(--color-black);
    border-radius: var(--radius-pill);
  }

  /* ---------- Tablet ---------- */
  @media (max-width: 1024px) {
    .stage { gap: 32px; padding: 32px 16px; }
    :root { --screen-scale: 0.95; }
  }

  /* ---------- Mobile ---------- */
  @media (max-width: 768px) {
    .stage { flex-direction: column; align-items: center; gap: 24px; padding: 20px 0; }
    :root { --screen-scale: 1; }
  }
  @media (max-width: 420px) { :root { --screen-scale: 0.92; } }
  @media (max-width: 380px) { :root { --screen-scale: 0.84; } }
  @media (max-width: 345px) { :root { --screen-scale: 0.76; } }
</style>
</head>
<body>
  <main class="stage">
    <h1 class="visually-hidden">iMessage screens</h1>

    <!-- Screen 1: Messages list -->
    <section class="device" aria-label="Messages list">
      <div class="messages">

        <ul class="pins">
          <li class="pin pin--col-1 pin--row-1">
            <div class="pin__avatar">
              <div class="pin__crop"><img class="pin__img" src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/49dd8.png" alt="Profile photo of nintuy"></div>
            </div>
            <div class="pin__contact">
              <img class="pin__badge" src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/9aee1.svg" alt="Unread">
              <p class="pin__name">nintuy</p>
            </div>
          </li>

          <li class="pin pin--col-2 pin--row-1">
            <div class="pin__avatar">
              <img class="pin__img pin__img--cover" src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/6c8dc.png" alt="Profile photo of ayayi">
            </div>
            <div class="pin__contact">
              <img class="pin__badge" src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/9aee1.svg" alt="Unread">
              <p class="pin__name">ayayi</p>
            </div>
          </li>

          <li class="pin pin--col-3 pin--row-1">
            <div class="pin__avatar">
              <div class="pin__crop"><img class="pin__img" src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/f7d7f.png" alt="Profile photo of ka muthee"></div>
            </div>
            <div class="pin__contact">
              <p class="pin__name">ka muthee</p>
            </div>
          </li>

          <li class="pin pin--col-1 pin--row-2">
            <div class="pin__avatar">
              <div class="pin__crop"><img class="pin__img" src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/bba55.png" alt="Profile photo of ka jessiii"></div>
            </div>
            <div class="pin__contact">
              <p class="pin__name">ka jessiii</p>
            </div>
          </li>

          <li class="pin pin--col-2 pin--row-2">
            <div class="pin__avatar">
              <div class="pin__crop"><img class="pin__img" src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/bd52e.png" alt="Profile photo of ribi"></div>
            </div>
            <div class="pin__contact">
              <p class="pin__name">ribi</p>
            </div>
          </li>

          <li class="pin pin--col-3 pin--row-2">
            <div class="pin__avatar pin__avatar--cover">
              <span class="pin__emoji" role="img" aria-label="Guitar">🎸</span>
            </div>
            <div class="pin__contact">
              <img class="pin__badge" src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/9aee1.svg" alt="Unread">
              <p class="pin__name">lepii&nbsp;</p>
            </div>
          </li>

          <li class="pin pin--col-1 pin--row-3 pin--group">
            <div class="pin__avatar pin__avatar--group">
              <div class="pin__avatars">
                <div class="pin__ellipse pin__ellipse--1"><img src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/a2b62.png" alt="Group member 1"></div>
                <div class="pin__ellipse pin__ellipse--2"><img src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/1d6ee.png" alt="Group member 2"></div>
                <div class="pin__ellipse pin__ellipse--3"><img src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/5c9e7.png" alt="Group member 3"></div>
                <div class="pin__ellipse pin__ellipse--4"><img src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/c51ea.png" alt="Group member 4"></div>
              </div>
            </div>
            <div class="pin__contact">
              <p class="pin__name">#GUEPASSION</p>
            </div>
          </li>

          <li class="pin pin--col-2 pin--row-3">
            <div class="pin__avatar">
              <div class="pin__crop"><img class="pin__img pin__img--aiz-1" src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/3f413.png" alt="Memoji of ka aiz"></div>
              <img class="pin__img pin__img--cover" src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/061e5.png" alt="">
              <div class="pin__crop"><img class="pin__img pin__img--aiz-3" src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/6e584.png" alt=""></div>
            </div>
            <div class="pin__contact">
              <p class="pin__name">ka aiz</p>
            </div>
          </li>

          <li class="pin pin--col-3 pin--row-3">
            <div class="pin__avatar">
              <div class="pin__crop"><img class="pin__img pin__img--atinn" src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/45ecc.png" alt="Memoji of ka atinn"></div>
            </div>
            <div class="pin__contact">
              <img class="pin__badge" src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/9aee1.svg" alt="Unread">
              <p class="pin__name">ka atinn&nbsp;</p>
            </div>
          </li>
        </ul>

        <ul class="messages__list">
          <li class="message message--first">
            <img class="message__avatar" src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/83dc5.png" alt="Profile photo of ka jessiii">
            <h2 class="message__name">ka jessiii</h2>
            <p class="message__text">nitip dubai cuwi gak? ada nih<br>3 di aku</p>
            <div class="message__time">
              <time class="message__time-text">1:20 PM</time>
              <span class="message__chevron message__chevron--partial"><img src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/4af03.svg" alt=""></span>
            </div>
            <div class="message__divider"></div>
          </li>

          <li class="message">
            <img class="message__avatar" src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/c430a.png" alt="Profile photo of ayayi">
            <h2 class="message__name">ayayi</h2>
            <p class="message__text">BANGUNIN JAM 2 SIANG PLS</p>
            <div class="message__time">
              <time class="message__time-text">11:44 AM</time>
              <span class="message__chevron"><img src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/90d57.svg" alt=""></span>
            </div>
            <div class="message__divider"></div>
          </li>

          <li class="message">
            <div class="message__group">
              <div class="message__ellipse message__ellipse--1"><img src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/fa01a.png" alt="Group member 1"></div>
              <div class="message__ellipse message__ellipse--2"><img src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/e3a95.png" alt="Group member 2"></div>
              <div class="message__ellipse message__ellipse--3"><img src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/187a2.png" alt="Group member 3"></div>
              <div class="message__ellipse message__ellipse--4"><img src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/ddc82.png" alt="Group member 4"></div>
            </div>
            <h2 class="message__name">#GUEPASSION</h2>
            <p class="message__text">WKWKWKWK</p>
            <div class="message__time">
              <time class="message__time-text">11:24 AM</time>
              <span class="message__chevron"><img src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/90d57.svg" alt=""></span>
            </div>
            <div class="message__divider"></div>
          </li>

          <li class="message">
            <img class="message__avatar" src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/fc38b.png" alt="Profile photo of ka muthee">
            <h2 class="message__name">ka muthee</h2>
            <p class="message__text">oke dd</p>
            <div class="message__time">
              <time class="message__time-text">8:14 AM</time>
              <span class="message__chevron"><img src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/90d57.svg" alt=""></span>
            </div>
            <div class="message__divider"></div>
          </li>

          <li class="message">
            <img class="message__avatar" src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/48582.png" alt="Profile photo of Greg Adams">
            <h2 class="message__name">Greg Adams</h2>
            <p class="message__text">Famers market is at Pasadena Highschool Saturday morning</p>
            <div class="message__time">
              <time class="message__time-text">11:30 PM</time>
              <span class="message__chevron"><img src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/90d57.svg" alt=""></span>
            </div>
            <div class="message__divider"></div>
          </li>
        </ul>

        <div class="home-indicator" aria-hidden="true"></div>

        <div class="bubble">
          <div class="bubble__shape"><img src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/da91b.svg" alt=""></div>
          <p class="bubble__text">LAPEEEERRRR</p>
        </div>

        <div class="reaction">
          <img src="https://www.figma.com/api/mcp/asset/a9f0a8f3-5a09-4279-91c9-3672bcbc6b26/ecdac.svg" alt="Heart reaction">
        </div>

        <form class="search" role="search" onsubmit="return false">
          <div class="search__field">
            <div class="search__bg"></div>
            <input class="search__input" type="search" placeholder="Search" aria-label="Search messages">
          </div>
        </form>

        <header class="nav">
          <button class="nav__edit" type="button">Edit</button>
          <h2 class="nav__title">Messages</h2>
        </header>
      </div>

      <div class="status-bar" aria-hidden="true">
        <div class="status-bar__time"><p class="status-bar__time-text">9:41</p></div>
        <div class="status-bar__island-wrap"><div class="status-bar__island"></div></div>
        <div class="status-bar__levels">
          <div class="status-bar__cellular">
            <span class="status-bar__bar status-bar__bar--1"></span>
            <span class="status-bar__bar status-bar__bar--2"></span>
            <span class="status-bar__bar status-bar__bar--3"></span>
            <span class="status-bar__bar status-bar__bar--4"></span>
          </div>
          <img class="status-bar__wifi" src="https://www.figma.com/api/mcp/asset/31ec062d-a97f-48b0-bb34-bad8b5e817b7/58037.svg" alt="">
          <img class="status-bar__battery" src="https://www.figma.com/api/mcp/asset/31ec062d-a97f-48b0-bb34-bad8b5e817b7/96802.svg" alt="">
        </div>
      </div>
    </section>

    <!-- Screen 2: Single chat -->
    <section class="device" aria-label="Chat with ka jessiii">
      <div class="chat">
        <header>
          <div class="chat__nav-shape"></div>

          <div class="chat__avatar">
            <img src="https://www.figma.com/api/mcp/asset/0fee230c-94bd-4980-b45c-0aa10f1b9028/bba55.png" alt="Profile photo of ka jessiii">
          </div>

          <div class="chat__title">
            <p class="chat__title-text">ka jessiii  </p>
            <img class="chat__chevron" src="https://www.figma.com/api/mcp/asset/0fee230c-94bd-4980-b45c-0aa10f1b9028/91cb3.svg" alt="">
          </div>

          <div class="chat-status" aria-hidden="true">
            <p class="chat-status__time">9:41</p>
            <span class="chat-status__battery"><img src="https://www.figma.com/api/mcp/asset/0fee230c-94bd-4980-b45c-0aa10f1b9028/4d743.svg" alt=""></span>
            <span class="chat-status__wifi"><img src="https://www.figma.com/api/mcp/asset/0fee230c-94bd-4980-b45c-0aa10f1b9028/8507c.svg" alt=""></span>
            <span class="chat-status__cellular"><img src="https://www.figma.com/api/mcp/asset/0fee230c-94bd-4980-b45c-0aa10f1b9028/f3f72.svg" alt=""></span>
          </div>

          <button class="chat__back" type="button" aria-label="Back to messages">
            <img src="https://www.figma.com/api/mcp/asset/0fee230c-94bd-4980-b45c-0aa10f1b9028/a3196.svg" alt="">
          </button>

          <button class="chat__facetime" type="button" aria-label="Start FaceTime video call">
            <img src="https://www.figma.com/api/mcp/asset/0fee230c-94bd-4980-b45c-0aa10f1b9028/7ac8c.svg" alt="">
          </button>
        </header>

        <form class="chat__composer" onsubmit="return false">
          <input class="chat__field" type="text" placeholder="iMessage" aria-label="iMessage">
          <button class="chat__add" type="button" aria-label="Add attachment">
            <img src="https://www.figma.com/api/mcp/asset/0fee230c-94bd-4980-b45c-0aa10f1b9028/d9c12.svg" alt="">
          </button>
        </form>

        <div class="chat__home-indicator" aria-hidden="true"></div>
      </div>
    </section>
  </main>
</body>
</html>
