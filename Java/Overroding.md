```java
package com.ssafy.newstar.domain.article.dto;

import com.ssafy.newstar.domain.article.entity.Article;
import java.time.LocalDateTime;
import lombok.Data;
import lombok.ToString;
import org.springframework.data.domain.Slice;

@Data
@ToString
public class ArticleResponse {

  Long article_id;

  private String title;

  private String url;

  private LocalDateTime date;

  private int Bcategory;

  private int Scategory;

  private String image_url;

  private String content;


  public static ArticleResponse createArticleResponse(Article article) {
    ArticleResponse articleResponse = new ArticleResponse();
    articleResponse.article_id = article.getId();
    articleResponse.title = article.getTitle();
    articleResponse.url = article.getUrl();
    articleResponse.date = article.getDate();
    articleResponse.Bcategory = article.getBcategory();
    articleResponse.Scategory = article.getScategory();
    articleResponse.image_url = article.getImageUrl();
    articleResponse.content = article.getSummary();
    return articleResponse;
  }

  public static Slice<ArticleResponse> createArticleResponse(Slice<Article> articles) {
    return articles.map(ArticleResponse::createArticleResponse);
  }
}
```

이번 프로젝트를 진행하며

Builder , Constructor, Factory Method 의 객체 생성 방법에 대해서 고민하게 되었습니다.

상속받아서 사용시킬때 외부에서 내부의 생성 방법을 명확하게 만들고, 필요한 파라미터를 명시화 하는것이 중요하다고 생각하기에

저는 팩토리 메서드를 이용해서 구현했습니다.

이때 List 로 랜더링이 필요한 경우와 하나의 객체를 랜더링 해야하는 경우를 구분하기 위해서

오버로딩을 직접 구현해본 경우입니다 !
