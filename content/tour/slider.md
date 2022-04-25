---
widget: slider
weight: 1
active: true
headless: true

design:
  # Slide height is automatic unless you force a specific height (e.g. '400px')
  slide_height: ''
  is_fullscreen: true
  # Automatically transition through slides?
  loop: false
  # Duration of transition between slides (in ms)
  interval: 2000

content:
  slides:
    - title: 👋 歡迎光臨TCPSR網站
      content: 向右捲動認識TCPSR...
      align: center
      background:
        position: right
        color: '#666'
        brightness: 0.7
     #  media: coders.jpg
    - title: TCPSR的任務 
      content: '推動可信有效心理學知識的正向循環！'
      align: left
      background:
        position: center
        color: '#555'
        brightness: 0.7
    - title: 最新成員 
      content: '協作群老師與同學來自的學校！'
      align: left
      background:
        position: center
        color: '#444'
        brightness: 0.7
    #    media: contact.jpg
    - title: 加入我們
      content: '提昇心理科學的透明度需要你的參與！'
      align: right
      background:
        position: center
        color: '#333'
        brightness: 0.5
    #    media: welcome.jpg
      link:
        icon: graduation-cap
        icon_pack: fas
        text: Join Us
        url: ../contact/
---
