# My Favourite Angular Interview Questions

### Q1: What is content projection and write pseudo code to do content projection?
Ans: Content projection is used to project some portion of content from parent component to child component. This will be greatly helpful when implementing the reusable countries.

We need to use ng-content in child component html page to project the content from the parent component.

### Q2: What is the difference between @ViewChild and @ContentChild? What are all can be accessed using @ViewChild in the component?
Ans: @ViewChild is used to access the child components/directives/html elements of the component HTML

@ContentChild is used to access the parent elements that got projected into parent component
using @ViewChild, you can access Component, Direactives, and any HTML elements.

### Q3: How to load a module lazily? Please write the pseudo code for lazy loading a module?

### Q4: What is the difference between View and Content in Angular terminology?
Ans: View always represents the HTML associated with the component HTML where as content refer to the content that we are projecting from parent component to child component.

### Q5: What is template reference variable and how to define that in angular?

Ans: Template reference variables used to access the HTML elements on the component. It is represented as `#<<refName>>` in component html

### Q6: What are all the different ways angular provides facilitate the communication between the two below mentioned scenarios? Please write pseudo code?

#### Parent to child
@Input is used to send the information from Parent component to child component.

#### Child to Parent
@Output is used to send the information from Child component to parent component in the form of events. i.e. Parent component has to define the event when defining the child component in html.

#### Independent components
This can be done using Service using Subject.

### Q7: When do you need to use patchValue and setValue in forms. Please explain?

Ans: patchValue will be used when updating the partial fields in the form where as setvalue is used to update all the fields in the form.

### Q8: What are all the different control states we have for a form control?

•	Dirty
•	Pristine
•	Touched
•	Untouched
•	Valid
•	Invalid

### Q9: When do we need to use the constructor and ngOnInit in angular?
Constructor is recommended to use to initialize the dependencies of the component where as ngOnInit is used to make required Service calls required for component HTML.
Please note that if your component has any input variables, those input values will not be available in the constructor. It is always recommended to go with the 'ngOnInIt' for you component initialization logic.

### Q10: What are all the different guards we have in angular? Please explain each guard in simple definitions?
Ans:
canActivate – Checks whether the user has the required permission to load the requested URL
canDeactivate – Checks whether there are any unsaved information
canLoad – Checks whether the user has the required permission to load the module
canChildActivate – Checks whether the user has the permisisons to load the child paths
resolve – provides the data before resolving the route

### Q11: What are all the different ways angular provides to send the parameters in routes. Please write the pseudo code for HTML and component level navigation.

Using Path parameters, Optional parameters, query string parameters, and navigationExtras.

### Q12: What is activated route service and why do we need to use that? And pseudo code to access the parameters?

Activate route service is used to access the parameters / data from the route.

### Q13: What are all the life cycle events available for Angular components?
•	ngOnChanges
•	ngOnInit
•	ngDoCheck
•	ngAfterContentInit
•	ngAfterContentChecked
•	ngAfterViewInit
•	ngAfterViewChecked
•	ngDestroy

### Q14: What are the different errors can occur in client-side application? How do we centralize the errors in Angular?
Ans:
HttpErrors
ClientErrors

Using GlobalError handler, you can cenralize the exception handling in your angular application.

### Q15: What is @Hostlistener and @Hostbinding?
@HostListener – used to listen certain events on the host element
@HostBinding – used to assign the values from directive or component for the host attributes

### Q16: How to retrieve the parameters when loading same component with different parameters? Please write pseudo code.

activateRouteService.paramMap.subscribe(x=>{
console.log(x.id);
});

### Q17: What is the difference between for in and for of. When do we need to use them?
Ans:
For in is used to loop over properties of an object
For of is used loop over array of elements

### Q18: What is the usage of ngNonBindable directive?
Ans: ngNonBindable used to exclude angular parsing of a specific text.

### Q19: What is stream and please define hot and cold stream?
Stream is data values over time
When there are no subscribers, a stream is called as a cold stream
When there are one more subscribers, a stream is called as hot stream

### Q20: What is pipe and how do you call a pipe with parameters?
Pipe is used to transform the values. We can use : to pass multiple parameters

import com.fasterxml.jackson.core.JsonProcessingException;
import com.fasterxml.jackson.databind.DeserializationFeature;
import com.fasterxml.jackson.databind.ObjectMapper;
import com.tm.common.constants.Constants;
import com.tm.common.jwt.JwtUtility;
import com.tm.common.security.annotations.AllowAnonymous;
import io.jsonwebtoken.Claims;
import org.apache.commons.collections.CollectionUtils;
import org.apache.commons.lang3.StringUtils;
import org.owasp.esapi.ESAPI;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.slf4j.MDC;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.http.*;
import org.springframework.security.authentication.UsernamePasswordAuthenticationToken;
import org.springframework.security.core.Authentication;
import org.springframework.security.core.authority.SimpleGrantedAuthority;
import org.springframework.security.core.context.SecurityContextHolder;
import org.springframework.stereotype.Component;
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.client.RestTemplate;
import org.springframework.web.method.HandlerMethod;
import org.springframework.web.servlet.HandlerInterceptor;
import org.springframework.web.servlet.ModelAndView;

import javax.annotation.PostConstruct;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.lang.reflect.Method;
import java.util.*;

@Component("Authorization")
public class AuthorizationRequestInterceptor implements HandlerInterceptor {

    private static final Logger LOGGER = LoggerFactory.getLogger(AuthorizationRequestInterceptor.class);

    private static final String REQUEST = "REQUEST";
    public static final String AUTHORIZATION = "Authorization";

    @Value("${userInfoEndpoint}")
    private String userInfoEndpoint;

    @Value("${jwtSecretKey:lUYhe38sF7Rs4aYW0xZZp}")
    private String jwtSecretKey;

    private static String getClientIpAddress(HttpServletRequest request) {
        String remoteAddr = "";
        if (Objects.nonNull(request)) {
            remoteAddr = request.getHeader("X-FORWARDED-FOR");
            if (Objects.isNull(remoteAddr) || StringUtils.isBlank(remoteAddr)) {
                remoteAddr = request.getRemoteAddr();
            } else {
                remoteAddr = remoteAddr.split(",")[0];
            }
        }
        return remoteAddr;
    }

    @PostConstruct
    public void init() {
        LOGGER.info(ESAPI.encoder().encodeForHTML("AuthorizationRequestInterceptor initiated..."));
    }

    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
        if (anonymousAccessAllowed(request, handler)) {
            setAnonymousSecurityContextToRequest();
            return true;
        }
        if (!authorizeRequest(request, response)) {
            return authorizationFailed(request, response, "Invalid Token");
        }
        return true;
    }

    @Override
    public void postHandle(HttpServletRequest request, HttpServletResponse response, Object handler, ModelAndView modelAndView) throws Exception {
        LOGGER.trace(ESAPI.encoder().encodeForHTML("Executing the postHandle method of AuthorizationRequestInterceptor"));
        MDC.clear();
    }

    // Whitelisting Hystrix calls
    private boolean isHystrixRequest(HttpServletRequest request, HttpServletResponse response) {
        return request.getRequestURI().split("/")[1].contains("hystrix");
    }

    private boolean anonymousAccessAllowed(HttpServletRequest request, Object handler) {
        if (handler instanceof HandlerMethod) {
            HandlerMethod handlerMethod = (HandlerMethod) handler;
            Method method = handlerMethod.getMethod();
            if (request.getDispatcherType().name().equals(REQUEST) && (method.getDeclaringClass().isAnnotationPresent(Controller.class)
                    || method.getDeclaringClass().isAnnotationPresent(RestController.class))) {
                if (method.isAnnotationPresent(AllowAnonymous.class) || method.getDeclaringClass().isAnnotationPresent(AllowAnonymous.class)) {
                    return Boolean.TRUE;
                }
            }
        }
        return Boolean.FALSE;
    }

    private Boolean authorizationFailed(HttpServletRequest request, HttpServletResponse response, String message) throws IOException, ServletException {
        response.sendError(401, message);
        LOGGER.error(ESAPI.encoder().encodeForHTML("Request Authenticity failed"));
        return Boolean.FALSE;
    }

    private boolean authorizeRequest(HttpServletRequest request, HttpServletResponse response) throws IOException, ServletException {
        if (request.getMethod().equals(RequestMethod.OPTIONS.toString())) {
            response.setStatus(HttpServletResponse.SC_OK);
            return true;
        }
        return validateRequestAndSetContext(request, response);
    }

    private boolean validateRequestAndSetContext(HttpServletRequest request, HttpServletResponse response) {
        String authorizationHeader = request.getHeader(AUTHORIZATION);
        boolean isValid = false;
        if (StringUtils.isNotBlank(authorizationHeader)) {
            if (isValidAuthorizationType(authorizationHeader)) {
                String authToken = extractBearerToken(authorizationHeader);
                if (StringUtils.isNotBlank(authToken)) {
                    Optional<Claims> claims = validateJwtAndExtractClaims(authToken);
                    if (claims.isPresent()) {
                        String subject = claims.get().getSubject();
                        Long userId = claims.get().get("Id", Long.class);
                        Optional<UserRequestContextPrincipal> userDetails = getUserDetails(userId);
                        if (userDetails.isPresent()) {
                            setSecurityContextToRequest(userDetails.get());
                            isValid = true;
                        }
                    }
                }
            }
        }
        if (!isValid) {
            try {
                response.sendError(401, "Invalid Token");
            } catch (IOException e) {
                e.printStackTrace();
            }
            LOGGER.error(ESAPI.encoder().encodeForHTML("Invalid request"));
        }
        return isValid;
    }

    private Optional<UserRequestContextPrincipal> getUserDetails(Long userId) {
        RestTemplate template = new RestTemplate();
        HttpHeaders headers = new HttpHeaders();
        UserRequestContextPrincipal userRequestContextPrincipal = new UserRequestContextPrincipal();
        headers.setAccept(Arrays.asList(MediaType.APPLICATION_JSON));
        HttpEntity<String> entity = new HttpEntity<String>("parameters", headers);
        ResponseEntity response = template.exchange(userInfoEndpoint + 1, HttpMethod.GET, entity, String.class);
        if (response.getStatusCodeValue() == 200) {
            try {
                ObjectMapper objectMapper = new ObjectMapper();
                objectMapper.disable(DeserializationFeature.FAIL_ON_UNKNOWN_PROPERTIES);
                userRequestContextPrincipal = objectMapper.readValue(response.getBody().toString(), UserRequestContextPrincipal.class);
            } catch (JsonProcessingException e) {
                e.printStackTrace();
                LOGGER.error(e.getMessage(), e.toString());
            }
            return Optional.of(userRequestContextPrincipal);
        }
        return Optional.empty();
    }

    private Boolean isValidAuthorizationType(String token) {
        Boolean status = Boolean.FALSE;
        if (StringUtils.isNotBlank(token)) {
            String tokens[] = token.split(Constants.Authorization.SPACE);
            if (tokens.length == 2) {
                token = tokens[0];
                if (token.equalsIgnoreCase(Constants.Authorization.BEARER_TOKEN)) {
                    status = Boolean.TRUE;
                }
            }
        }
        return status;
    }

    private Optional<Claims> validateJwtAndExtractClaims(String jwtToken) {
        try {
            //TODO: when secret key is empty, need to extract the account id from the
            // JWT and get secret key from DB based on account Id
            Claims claims = JwtUtility.decodeJWT(jwtToken, jwtSecretKey);
            return Optional.of(claims);
        } catch (Exception ex) {
            LOGGER.error(ex.getMessage(), ex.toString());
        }
        return Optional.empty();
    }

    private String extractBearerToken(String authorizationHeaderValue) {
        if (StringUtils.isNotBlank(authorizationHeaderValue)) {
            String[] tokens = authorizationHeaderValue.split(Constants.Authorization.SPACE);
            if (tokens.length > 1) {
                return tokens[1];
            }
        }
        return StringUtils.EMPTY;
    }

    private void setSecurityContextToRequest(UserRequestContextPrincipal userSecurityContextModel) {
        if (Objects.nonNull(userSecurityContextModel)) {
            List<SimpleGrantedAuthority> updatedPermissions = fillInGrants(userSecurityContextModel);
            Authentication auth = new UsernamePasswordAuthenticationToken(userSecurityContextModel, null, updatedPermissions);
            SecurityContextHolder.getContext().setAuthentication(auth);
        }
    }

    private void setAnonymousSecurityContextToRequest() {
        UserRequestContextPrincipal userSecurityContextModel = new UserRequestContextPrincipal();
        List<SimpleGrantedAuthority> updatedPermissions = fillInGrants(userSecurityContextModel);
        Authentication auth = new UsernamePasswordAuthenticationToken(userSecurityContextModel, null, updatedPermissions);
        SecurityContextHolder.getContext().setAuthentication(auth);
    }


    private List<SimpleGrantedAuthority> fillInGrants(UserRequestContextPrincipal userRequestContextPrincipal) {
        List<SimpleGrantedAuthority> securityGrants = new ArrayList<>();
        if (Objects.nonNull(userRequestContextPrincipal) && CollectionUtils.isNotEmpty(userRequestContextPrincipal.getPrivileges())) {
            userRequestContextPrincipal.getPrivileges().forEach(item ->
                    securityGrants.add(new SimpleGrantedAuthority(item.getCode())));
        } else {
            securityGrants.add(new SimpleGrantedAuthority("Anonymous"));
        }
        return securityGrants;
    }
}
