JEE  
Poziomy rozróżniane w ramach platformy Jakarta EE:

- poziom klienta - (client tier) uruchamiana na maszynie klienta (użytkownika):
    - samodzielne aplikacje okienkowe,
    - strony internetowe renderowane w przeglądarce;
- poziom webowy - (web tier) uruchamiana na serwerze aplikacji:
    - mechanizmy generowania dynamicznych stron internetowych, np.: JavaServer Faces (JSF) lub JavaServer Pages (JSP);
- poziom biznesowy - (business tier) uruchamiana na serwerze aplikacji:
    - implementacja logiki biznesowej,
- poziom danych - (Enterprise Information System) uruchomiona na serwerze EIS:
    - źródło danych

&nbsp;

### **Kontener** - elementy platformy Jakarta EE sterujące wykonaniem komponentów znajdujących się na poszczególnych poziomach.

- kontener webowy - uruchomiony po stronie serwera aplikacji, steruje cyklem życia servletów i stron JSF/JSP,
- kontener EJB - uruchomiony po stronie serwera aplikacji, steruje cyklem życia wszystkich komponentów EJB,
- kontener kliencki - uruchomiony po stronie klienta, steruje wykonaniem aplikacji klienckiej,
- kontener apletów - uruchomiony po stronie klienta w kontekście przeglądarki internetowej, steruje wykonaniem apletów (deprecated) osadzonych na stronach internetowych.

&nbsp;

### Relacje:

- tylko komponenty EJB (kontener EJB) powinny mieć dostęp do źródła danych (np.: baza danych),
- komponenty JSF/JSP i servlety (kontener webowy) powinny wywoływać odpowiednie metody z komponentów EJB w celu zrealizowania operacji biznesowych,
- strony internetowe wyświetlane przez przeglądarkę są generowane przez komponenty JSF/JSP,
- dodatkowo żądania HTTP mogą być realizowane przez servlety,
- aplikacje klienckie (kontener kliencki) odwołują się bezpośrednio do komponentów EJB.

&nbsp;

**Profile Jakarta EE** określają jakie funkcje musi posiadać serwer aplikacji, aby uzyskać certyfikat zgodności z platformą Jakarta EE.

- Full Profile (Platform),
- Web Profile (od Java EE 6): profil przeznaczony dla aplikacji WWW (stron internetowych)
- Core Profile (od Jakarta EE 10):

**Web/Servlet container** - komponent serwera webowego zajmującego się interakcją z servletami i potencjalnie stronami  JSP. np **Apache Tomcat 10.1.x**

&nbsp;

## **W pom.xml**

**Zależność dla Jakarta EE musi być ustawiona jako provided ponieważ jest dostarczana po stronie serwera.**

**Wymagany jest plugin generujący archiwum war.**

> &lt;plugin&gt;  
> &lt;groupId&gt;org.apache.maven.plugins&lt;/groupId&gt;  
> &lt;artifactId&gt;maven-war-plugin&lt;/artifactId&gt;  
> &lt;version&gt;3.3.2&lt;/version&gt;  
> &lt;/plugin&gt;

&nbsp;

&nbsp;