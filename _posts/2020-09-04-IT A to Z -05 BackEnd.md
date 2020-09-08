---
layout: post
title: "[NOTE] IT A to Z -05 BackEnd"
date: 2020-09-04 00:00:00
categories: [FORTUNE]
tags: [NOTE]
last_modified_at: 2020-09-04
---

From [https://www.grabbing.me/69a68655ae9c46efaeae5014b9f9034d#467acb0ae8c34ab183d6e4bdb9204c76](https://www.grabbing.me/69a68655ae9c46efaeae5014b9f9034d#467acb0ae8c34ab183d6e4bdb9204c76)

---

### 1. 백엔드

<p>
: 서비스에 필요한 모든 데이터를 저장하고, 클라이언트를 위해 데이터를 가공하는 역할, 데이터가 중심.
</p>

---

### 2. 백엔드의 구성

<p>
: 여러가지 서버프로그램들이 유기적으로 연결되어 있음.
</p>

<br>

__데이터 베이스__

<p>
: 서비스에 필요한 데이터를 저장하는 역할.
<br>따라서 보안이 되게 중요함. DB에서 직접 정보를 가져올 수 있는 주체를 제한함.
</p>

<br>

__API서버__

<p>
: DB의 데이터를 가공해서 클라이언트에게 전달하는 역할을 함.
<br>* DB는 클라이언트의 접근을 막지만, 클라이언트에게 대신 데이터를 전달해주는 API서버에게는 연결을 허용.
<br>* 이를 위해 방화벽을 설정하고, 보안을 위해서 API서버(WAS서버),서비스 관리자들만 접근할 수 있게 함.
<br>* 웹, 앱에게 데이터를 제공하는 API서버를 WAS,Web Application Server라고 함.
</p>

<br>

__파일 스토리지__

<p>
: 파일들을 전문적으로 저장하는 서버로, 스토리지 서버에 파일들을 저상한 후 URL주소를 통해 다운받음.
<br>* DB에도 파일을 저장할 수 있지만, DB는 텍스트 위주로 이루어진 내용을 다루는 데 최적화.
</p>

<br>

__캐시 서버__

<p>
: Cache는 자주 쓰이는 정보를 저장해 놓는다는 개념.
<br>* API서버에게 항상 동일한 결과를 요청하면, 반복해서 API서버에서 DB의 정보를 가져와 가공할 필요가 없음.
<br>* 그래서 자주 쓰이는 데이터를 캐시서버에 저장해 API서버와 DB가 따로 일을 하지 않고, 바로 저장된 데이터를 제공해 줄 수 있음.
</p>

---

### 3. 클라우드

<p>
: 위의 백엔드는 전부 컴퓨터 안에서 동작, 클라우드는 기존에 회사에서 전부 관리하던 컴퓨터들을 클라우드 회사에서 관리하게 함.
<br>* 클라우드 회사의 가상화 기술을 바탕으로, 사용자들이 본인의 컴퓨터에서 네트워크 접속을 통해 클라우드의 컴퓨터들을 사용할 수 있게 됨.
</p>

<br>

__클라우드의 특징__
<p>
1. 서버 호스팅, 온라인으로 서버 컴퓨터를 빌릴 수 있음.
<br>2. 컴퓨터 간의 네트워크 설정을 손쉽게 할 수 있음, 웹사이트에서 보안설정이 가능.
<br>3. 컴퓨터의 성능을 자유롭게 설정할 수 있음.
<br>&emsp;: 네트워크 관점에서 클라이언트의 요청량을 트래픽이라함. 트레픽이 많아지면서 서버컴퓨터의 성능저하는 물론 응답시간이 길어짐.
따라서 더 많은 컴퓨팅 자원이 있어야 안정적인 서버운영이 가능. 클라우드에서는 트래픽에 대응해서 컴퓨팅 자원을 줄이거나 늘리는 스케일링 작업을 쉽게 해줌.
</p>

<br>

__백엔드와 클라우드__
<p>
* 대부분의 회사에서 백엔드 서버는 전부 클라우드로 관리.
<br>* 클라우드는 따로 서버 컴퓨터 관리를 하지 않아도 되고, 다양한 기능을 제공.
<br>대표적으로 AWS, DCP, Azure 등이 있음.
</p>

---

### 4. 백엔드 개발에 더 알고 있으면 좋을 것들

<br>

__서버 스케일링__

<p>
* 서버에 많은 요청이 들어온다. =  트래픽이 높아졌다.
<br>* 트레픽이 높아질 수록 자원이 부족해, 응답은 바로바로 못해주고 밀리는 병목현상이 발생.
<br>이를 해결하기 위해 스케일 업, 스케일 아웃, 또는 캐시 서버를 이용할 수 있음.
<br>1. 스케일 업
<br>&emsp;: 해당 서버의 컴퓨터 성능을 늘리는 것
<br>2. 스케일 아웃
<br>&emsp;: 서버를 여러대로 늘려, 트래픽을 분산시킴.
<br>
<br>* 이제는 클라우드에서 자동으로 스케일링을 해줌 : 오토 스케일링
<br>* 그래서 서버 개발자들이 서버를 계속 모니터링 하지 않아도 됨.

<br>* 서버입장에서 처리해야 할 일을 Load라고 함. 스케일 아웃을 통해 로드를 분산시키는 일 : 로드밸런싱
</p>

<br>

__모니터링__

<p>
: 서버의 컴퓨터 성능을 관찰하는 것
<br>* 서버컴퓨터의 상태를 지속적으로 점검할 수 있는 장치로 모니터링 장치가 필요.
<br>* 보통 API나 DB에 모니터링 장치를 사용.
</p>


<br>
<br>


