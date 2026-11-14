# KUSC 홈페이지 수정 방법 (후임 임원진용)

코딩을 몰라도 됩니다. **글자만 바꾸는 것**이 전부예요.

## 기본 정보

| 항목 | 내용 |
|---|---|
| 사이트 주소 | https://kusc-official.github.io |
| GitHub Organization | `kusc-official` (https://github.com/kusc-official) |
| 저장소 | https://github.com/kusc-official/kusc-official.github.io |
| 배포 방식 | GitHub Pages (`main` 브랜치에 올리면 1~2분 뒤 사이트에 자동 반영) |

임원진이 바뀌면 새 임원진을 Organization 멤버로 초대하고, 졸업한 임원진은 멤버에서 빼 주세요.

## 파일 구성

| 파일 | 하는 일 | 고칠 일 |
|---|---|---|
| `index.html` | 사이트에 보이는 **글** 전부 | 자주 고침 |
| `style.css` | 색·글자 크기·배치 등 **디자인** | 거의 없음 |
| `images/` | 로고, 활동 사진 | 사진 추가할 때 |

## GitHub에서 글자 고치는 법

1. GitHub 저장소에서 `index.html`을 누릅니다.
2. 오른쪽 위 연필 아이콘(✏️ Edit)을 누릅니다.
3. `Ctrl + F`로 바꾸고 싶은 문장을 찾아 글자를 고칩니다.
4. 오른쪽 위 **Commit changes** 버튼을 누릅니다.
5. 1~2분 뒤 사이트에 반영됩니다. 반영이 안 되어 보이면 새로고침(Ctrl + F5) 해 보세요.

## 꼭 지켜야 할 규칙

- `<` `>` 로 둘러싸인 부분(태그)은 건드리지 말고, **그 사이의 글자만** 바꾸세요.
  - 예: `<p>여기 글자만 바꾸기</p>`
- `<!-- ✏️ ... -->` 처럼 생긴 줄은 사이트에 보이지 않는 **안내 메모**입니다. 지워도 되고 남겨도 됩니다.
- 고치기 전에 내용을 메모장에 복사해 두면, 실수해도 되돌리기 쉽습니다.
  (GitHub에는 이전 버전이 모두 남아 있어서 History에서 되돌릴 수도 있어요.)

## 자주 하는 수정

### 1) 학기가 바뀌었을 때
- About의 **학회 구성 숫자 카드**: `26-2학기 활동 인원`, `40명` 등의 글자를 바꿉니다.
- Q&A 위쪽 **모집 안내** 상자의 일정과 학회비를 바꿉니다.

### 2) 활동 하나 추가하기
`index.html`에서 아래 묶음을 통째로 복사해 원하는 카테고리 안에 붙여넣고 글자만 바꿉니다.
(최신 활동을 위에 두고 있어요.)

```html
<details class="item">
  <summary>
    <span class="item-top"><span class="item-date">2027-1 · 3/10</span><span class="badge upcoming">예정</span></span>
    <span class="item-title">활동 제목</span>
    <span class="item-sum">한 줄 요약 (접혀 있을 때 보이는 문장)</span>
  </summary>
  <div class="item-detail">
    <ul>
      <li>펼쳤을 때 보이는 상세 내용 1</li>
      <li>상세 내용 2</li>
    </ul>
  </div>
</details>
```

### 3) 활동 상태 바꾸기 (예정 → 완료)
아래 셋 중 하나로 바꿔 쓰면 색이 자동으로 바뀝니다.

| 상태 | 이렇게 쓰기 |
|---|---|
| 완료 | `<span class="badge done">완료</span>` |
| 진행 중 | `<span class="badge ongoing">진행 중</span>` |
| 예정 | `<span class="badge upcoming">예정</span>` |

모집 안내 상자는 `<span class="badge closed">모집 마감</span>` / `<span class="badge open">모집 중</span>` 을 씁니다.

### 4) Q&A 질문 추가하기

```html
<details class="qa">
  <summary>질문을 여기에 쓰세요?</summary>
  <p>답변을 여기에 쓰세요.</p>
</details>
```

### 5) 사진 추가하기
1. GitHub 저장소의 `images` 폴더로 들어가 **Add file → Upload files**로 사진을 올립니다.
   - 파일 이름은 **영어 소문자·숫자·하이픈**을 권장합니다 (예: `2027-1-seminar.jpg`). 대문자/소문자를 구분하니 주의하세요.
2. 원하는 활동의 상세 내용 안에 아래 줄을 넣습니다.

```html
<div class="photos">
  <img src="images/2027-1-seminar.jpg" alt="사진 설명" loading="lazy">
</div>
```

⚠️ 사람 얼굴이 나온 사진은 사이트에 직접 올리지 않습니다. 대신 경영대학 홈페이지 등 외부 게시물로
`<a class="photo-link" href="주소" target="_blank" rel="noopener">행사 사진 보기 ↗</a>` 처럼 링크를 겁니다.
쓰지 않는 사진은 `사이트제외` 폴더에 보관하세요. 이 폴더는 GitHub에 올라가지 않습니다(`.gitignore`에 등록됨).

## 개인 계정 노출 주의
- 이 폴더에서 Git으로 올리는 기록은 작성자가 **KUSC**로 표시되도록 설정되어 있습니다.
- 하지만 **GitHub 웹사이트에서 직접 고치면** 그 순간 로그인한 계정 이름이 기록에 남습니다.
  개인 계정이 드러나지 않게 하려면 **학회 공용 GitHub 계정**으로 로그인해서 고치세요.

### 6) 색 바꾸기
`style.css` 맨 위 `:root { ... }` 안의 색 코드(`#1f2a55` 등)만 바꾸면 사이트 전체 색이 바뀝니다.

## 링크 미리보기 (카톡·인스타 공유)

`index.html` 맨 위의 `og:url`, `og:image` 두 줄에 사이트 주소(`https://kusc-official.github.io`)가 들어 있습니다.
사이트 주소가 바뀌면 이 두 줄도 함께 바꿔야 미리보기 이미지가 뜹니다.

- 카카오톡은 미리보기를 한동안 저장해 둡니다. 내용을 바꿨는데 예전 미리보기가 뜨면
  [카카오 공유 디버거](https://developers.kakao.com/tool/debugger/sharing)에서 주소를 넣고 "캐시 초기화"를 누르세요.
