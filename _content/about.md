---
layout: page
permalink: /about/
title: About
---

<style>
.about-container {
  display: flex;
  gap: 2rem;
  align-items: flex-start;
  margin: 2rem 0;
}
.about-image {
  flex-shrink: 0;
}
.about-image img {
  width: 180px;
  height: 180px;
  border-radius: 50%;
  object-fit: cover;
}
.about-content {
  flex: 1;
  min-width: 0;
}
.about-links {
  margin-top: 1.5rem;
  padding-top: 1rem;
  border-top: 1px solid #e0e0e0;
}
.about-links a {
  display: inline-block;
  margin-right: 1.5rem;
  text-decoration: none;
  color: #4fb1ba;
  font-weight: 500;
}
.about-links a:hover {
  text-decoration: underline;
}
@media (max-width: 640px) {
  .about-container {
    flex-direction: column;
    align-items: center;
    text-align: center;
  }
}
</style>

<div class="about-container">
  <div class="about-image">
    <img src="/assets/img/me_2023.jpg" alt="Profile">
  </div>
  <div class="about-content">
    <p>서울대학교 화학생물공학부에서 머신러닝으로 화학을 공부하고 있습니다.</p>
    <p>머리를 비우도록 도와주는 달리기나 배드민턴을 좋아합니다.</p>
    <div class="about-links">
      <a href="https://github.com/Gunwook-Nam" target="_blank">GitHub</a>
      <a href="mailto:gunwook@snu.ac.kr">Email</a>
    </div>
  </div>
</div>