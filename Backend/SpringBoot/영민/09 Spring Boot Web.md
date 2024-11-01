# Filter 와 Interceptor


```
package com.example.filter.fiilter;  
  
import jakarta.servlet.*;  
import jakarta.servlet.http.HttpServletRequest;  
import jakarta.servlet.http.HttpServletRequestWrapper;  
import jakarta.servlet.http.HttpServletResponse;  
import jakarta.servlet.http.HttpServletResponseWrapper;  
import lombok.extern.slf4j.Slf4j;  
import org.springframework.stereotype.Component;  
import org.springframework.web.util.ContentCachingRequestWrapper;  
import org.springframework.web.util.ContentCachingResponseWrapper;  
  
import java.io.IOException;  
import java.util.stream.Collectors;  
  
@Slf4j  
@Component  
public class LogerFilter implements Filter {  
  
    @Override  
    public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain) throws IOException, ServletException {  
        // 진입 전  
        log.info(" >>>>> 진입");  
        var req = new ContentCachingRequestWrapper((HttpServletRequest) request);  
        var res = new ContentCachingResponseWrapper((HttpServletResponse) response) {  
        };  
  
        chain.doFilter(req, res);  
  
        var reqjson = new String(req.getContentAsByteArray());  
        log.info("req : {} ", reqjson);  
        var resjson = new String(res.getContentAsByteArray());  
        log.info("res : {} ", resjson);  
  
  
        log.info(" <<<<< 리턴");  
        // 진입 후  
  
        res.copyBodyToResponse();  
  
    }  
}
```

커밋이되나? 이렇게 하다보면 자동으로 저장이 되는거야??
커밋해줘이이이잉이이잉
풀해줘어엉어어