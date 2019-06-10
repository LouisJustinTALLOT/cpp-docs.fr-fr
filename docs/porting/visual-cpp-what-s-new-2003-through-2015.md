---
title: Nouveautés de Visual C++ entre 2003 et 2015
ms.date: 11/04/2016
ms.assetid: c4afde6f-3d75-40bf-986f-be57e3818e26
ms.openlocfilehash: 4bcf661284d447b18542bb158940d539ef9c0686
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449808"
---
# <a name="visual-c-what39s-new-2003-through-2015"></a>Nouveautés de Visual C++ entre 2003 et 2015

Cette page regroupe toutes les pages « Nouveautés » de toutes les versions de Visual C++ en commençant par Visual Studio 2015 et en remontant jusqu’à la version 2003. Ces informations sont fournies à des fins pratiques, car elles peuvent se révéler utiles lors d’une mise à niveau à partir de versions antérieures de Visual Studio.

> [!NOTE]
> Pour plus d’informations sur la version actuelle de Visual Studio, consultez [Nouveautés de Visual C++ dans Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md) et [Améliorations de la conformité de Visual C++ dans Visual Studio](../overview/cpp-conformance-improvements.md).

## <a name="whats-new-for-c-in-visual-studio-2015"></a>Nouveautés de C++ dans Visual Studio 2015

Dans Visual Studio 2015 et ultérieur, les améliorations continues de la conformité du compilateur peuvent parfois modifier la façon dont le compilateur comprend votre code source existant. Dans ce cas, vous pouvez être confronté à des erreurs nouvelles ou différentes pendant la génération, ou même à des différences de comportement dans le code qui auparavant était généré et paraissait s’exécuter correctement.

Heureusement, ces différences n’ont que peu ou pas d’impact sur la plus grande partie de votre code source et, quand le code source ou d’autres modifications sont nécessaires pour résoudre ces différences, les corrections sont généralement mineures et simples. Nous avons inclus de nombreux exemples de code source précédemment acceptable qui devront peut-être être changés *(avant)* et les corrections pour les modifier *(après)* .

Même si ces différences peuvent affecter votre code source ou d’autres artefacts de build, elles n’affectent pas la compatibilité binaire entre les mises à jour des versions de Visual C++. Type plus sérieux de modification, la *modification avec rupture* peut affecter la compatibilité binaire, mais ces types d’incompatibilités binaires se produisent uniquement entre les versions principales de Visual C++, par exemple entre Visual C++ 2013 et Visual C++ 2015. Pour plus d’informations sur les modifications avec rupture qui se sont produites entre Visual C++ 2013 et Visual C++ 2015, consultez [Historique des modifications de Visual C++ entre 2003 et 2015](../porting/visual-cpp-change-history-2003-2015.md).

- [Améliorations de la conformité dans Visual Studio 2015](#VS_RTM)

- [Améliorations de la conformité dans Visual Studio 2015 Update 1](#VS_Update1)

- [Améliorations de la conformité dans Visual Studio 2015 Update 2](#VS_Update2)

- [Améliorations de la conformité dans Visual Studio 2015 Update 3](#VS_Update3)

### <a name="VS_RTM"></a> Améliorations de la conformité dans Visual Studio 2015

- **/Zc:forScope- option**

   L’option de compilateur `/Zc:forScope-` est dépréciée. Elle sera supprimée dans une version ultérieure.

   ```output
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
   ```

   Cette option était généralement utilisée pour autoriser du code non standard utilisant des variables de boucle après le point où, selon la norme, elles devraient être hors de portée. Elle était nécessaire uniquement en cas de compilation avec l’option `/Za`, car sans `/Za`, l’utilisation d’une variable de boucle for après la fin de la boucle est toujours autorisée. Si vous ne vous souciez pas de la conformité aux normes (par exemple, si le code n’est pas destiné à d’autres compilateurs), vous pouvez éventuellement désactiver l’option `/Za` (ou assigner à la propriété **Désactivation des extensions de langage** la valeur **Non**). Si vous souhaitez écrire un code portable, conforme aux normes, vous devez réécrire votre code afin qu'il soit conforme à la norme en déplaçant la déclaration de ces variables vers un point extérieur à la boucle.

   ```cpp
    // zc_forScope.cpp
    // compile with: /Zc:forScope- /Za
    // C2065 expected
    int main() {
       // Uncomment the following line to resolve.
       // int i;
       for (int i =0; i < 1; i++)
          ;
       i = 20;   // i has already gone out of scope under /Za
    }
   ```

- **Option de compilateur Zg.**

   L’option de compilateur `/Zg` (Générer des prototypes de fonction) n’est plus disponible. Cette option de compilateur a été déconseillée précédemment.

- Vous ne pouvez plus exécuter de tests unitaires avec C++/CLI à partir de la ligne de commande avec mstest.exe. À la place, utilisez vstest.console.exe.

- **Mot clé mutable.**

   Le spécificateur de classe de stockage **mutable** n’est plus autorisé dans les emplacements où il était compilé sans erreur. À présent, le compilateur attribue l'erreur C2071 (classe de stockage non conforme). Conformément à la norme, le spécificateur mutable peut être appliqué uniquement à des noms de données membres de classe. Il ne peut pas être appliqué à des noms déclarés const ou static, ni à des membres de référence.

   Considérons par exemple le code suivant :

   ```cpp
    struct S {
        mutable int &r;
    };
   ```

   Les versions précédentes du compilateur Microsoft C++ acceptaient cela, mais le compilateur affiche désormais l’erreur suivante :

   ```Output
    error C2071: 'S::r': illegal storage class
   ```

   Pour corriger l’erreur, supprimez simplement le mot clé **mutable** redondant.

- **char_16_t et char32_t**

   Vous ne pouvez plus utiliser `char16_t` ou `char32_t` comme alias dans un typedef, car ces types sont maintenant traités comme des types intégrés. Les utilisateurs et les auteurs de bibliothèques définissaient souvent `char16_t` et `char32_t` comme alias de `uint16_t` et `uint32_t`, respectivement.

   ```cpp
    #include <cstdint>

    typedef uint16_t char16_t; //C2628
    typedef uint32_t char32_t; //C2628

    int main(int argc, char* argv[])
    {
    uint16_t x = 1; uint32_t y = 2;
    char16_t a = x;
    char32_t b = y;
    return 0;
    }
   ```

   Pour mettre à jour le code, supprimez les déclarations **typedef** et renommez tous les autres identificateurs qui entrent en conflit avec ces noms.

- **Paramètres de modèle sans type**

   Du code qui implique des paramètres de modèle sans type fait à présent l'objet d'une vérification correcte de la compatibilité des types quand vous fournissez des arguments template explicites. Par exemple, le code suivant pouvait être compilé sans erreur dans les versions antérieures de Visual C++.

   ```cpp
    struct S1
    {
        void f(int);
        void f(int, int);
    };

    struct S2
    {
        template <class C, void (C::*Function)(int) const> void f() {}
    };

    void f()
    {
        S2 s2;
        s2.f<S1, &S1::f>();
    }
   ```

   Le compilateur actuel attribue normalement une erreur, car le type de paramètre de modèle ne correspond pas à l'argument template (le paramètre est un pointeur vers un membre const, mais la fonction f est non const) :

   ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
   ```

   Pour résoudre cette erreur dans votre code, assurez-vous que le type de l’argument template que vous utilisez correspond au type déclaré du paramètre de modèle.

- **__declspec(align)**

   Le compilateur n'accepte plus `__declspec(align)` sur les fonctions. Ceci était toujours ignoré, mais à présent cela génère une erreur du compilateur.

   ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
   ```

   Pour résoudre ce problème, supprimez `__declspec(align)` de la déclaration de fonction. Comme cela n'avait aucun effet, la suppression ne change rien.

- **Gestion des exceptions**

   Quelques modifications ont été apportées à la gestion des exceptions. Tout d'abord, les objets d'exception doivent pouvoir être copiés ou déplacés. Le code suivant se compile dans Visual Studio 2013, mais pas dans Visual Studio 2015 :

   ```cpp
    struct S {
    public:
        S();
    private:
        S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
   ```

   Le problème est que le constructeur de copie est privé, si bien que l'objet ne peut pas être copié comme dans le cours normal de la gestion d'une exception. Il en va de même quand le constructeur de copie est déclaré **explicit**.

   ```cpp
    struct S {
        S();
        explicit S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
   ```

   Pour mettre à jour votre code, vérifiez que le constructeur de copie de l’objet d’exception est public et qu’il n’est pas marqué **explicit**.

   L'interception d'une exception par sa valeur exige que l'objet d'exception puisse être copié. Le code suivant se compile dans Visual Studio 2013, mais pas dans Visual Studio 2015 :

   ```cpp
    struct B {
    public:
        B();
    private:
        B(const B &);
    };

    struct D : public B {
    };

    int main()
    {
        try
        {
        }
        catch (D d) // error
        {
        }
    }
   ```

   Vous pouvez résoudre ce problème en remplaçant le type de paramètre de **catch** par une référence.

   ```cpp
    catch(D& d)
    {
    }
   ```

- **Littéraux de chaîne suivis par des macros**

   Le compilateur prend désormais en charge les littéraux définis par l'utilisateur. Par conséquent, les littéraux de chaîne suivis par des macros sans espace blanc intermédiaire sont interprétés comme des littéraux définis par l'utilisateur, qui peuvent entraîner des erreurs ou des résultats inattendus. Par exemple, dans les compilateurs précédents, le code suivant pouvait être compilé avec succès :

   ```cpp
    #define _x "there"
    char* func() {
        return "hello"_x;
    }
    int main()
    {
        char * p = func();
        return 0;
    }
   ```

   Le compilateur interprétait cela comme un littéral de chaîne « hello » suivi par une macro, correspondant à « there » étendu, puis les deux littéraux de chaîne étaient concaténés en un seul. Dans Visual Studio 2015, le compilateur interprète cela comme un littéral défini par l’utilisateur, mais comme il n’existe aucun littéral _x correspondant défini par l’utilisateur, une erreur est générée.

   ```cpp
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?

   ```

   Pour résoudre ce problème, ajoutez un espace entre le littéral de chaîne et la macro.

- **Littéraux de chaîne adjacents**

   Comme précédemment, en raison des modifications associées dans l'analyse des chaînes, les littéraux de chaîne adjacents (littéraux de chaîne aux caractères larges ou étroits) sans espace blanc étaient interprétés comme une chaîne concaténée unique dans les versions antérieures de Visual C++. Dans Visual Studio 2015, vous devez maintenant ajouter un espace blanc entre les deux chaînes. Par exemple, le code suivant doit être modifié :

   ```cpp
    char * str = "abc""def";
   ```

   Ajoutez simplement un espace entre les deux chaînes.

   ```cpp
    char * str = "abc" "def";
   ```

- **Placement new et delete**

   Une modification a été apportée à l’opérateur **delete** pour le rendre conforme à la norme C++14. Vous trouverez les détails relatifs au changement de normes sur la page décrivant la [libération dimensionnée C++](https://isocpp.org/files/papers/n3778.html). Les changements ajoutent une forme de l’opérateur **delete** global, qui accepte un paramètre de taille. Il s’agit d’un changement cassant pour la raison suivante : si vous utilisiez un opérateur **delete** avec la même signature (pour correspondre à un opérateur **placement new**), vous recevrez une erreur de compilation (C2956, qui se produit au point où l’opérateur **placement new** est utilisé, car il s’agit de la position dans le code où le compilateur tente d’identifier l’opérateur **delete** correspondant approprié).

   La fonction `void operator delete(void *, size_t)` était un opérateur **placement delete** correspondant à la fonction **placement new** `void * operator new(size_t, size_t)` dans C++11. Avec la libération dimensionnée C++14, cette fonction **delete** est à présent une *fonction de libération habituelle* (opérateur **delete** global). Selon la norme, si l’utilisation d’un opérateur **placement new** recherche une fonction **delete** correspondante et trouve une fonction de libération habituelle, le programme est incorrect.

   Par exemple, votre code définit à la fois un opérateur **placement new** et un opérateur **placement delete** :

   ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;
   ```

   Le problème se produit en raison de la correspondance dans les signatures de fonction entre un opérateur **placement delete** que vous avez défini et le nouvel opérateur **delete** dimensionné global. Déterminez si vous pouvez utiliser un autre type que `size_t` pour les opérateurs **placement new** et **delete**.  Notez que le type du **typedef** `size_t` dépend du compilateur. Il s’agit d’un **typedef** pour **unsigned int** en Visual C++. Il est recommandé d'utiliser un type énuméré tel que :

   ```cpp
    enum class my_type : size_t {};
   ```

   Changez ensuite votre définition de placement **new** et **delete** pour utiliser ce type en tant que second argument à la place de `size_t`. Vous devez également mettre à jour les appels à **placement new** afin de passer le nouveau type (par exemple, en utilisant `static_cast<my_type>` pour effectuer une conversion à partir de la valeur entière) et mettre à jour la définition de **new** et **delete** pour réeffectuer un cast vers le type entier. Vous n’avez pas besoin d’utiliser un **enum** pour cela. Un type de classe avec un membre `size_t` fonctionne également.

   Une autre solution consiste à éliminer complètement **placement new**. Si votre code utilise **placement new** pour implémenter un pool de mémoires où l’argument de positionnement correspond à la taille de l’objet alloué ou supprimé, la fonction de libération dimensionnée peut servir à remplacer votre propre code de pool de mémoires personnalisé. De plus, vous pouvez supprimer les fonctions de positionnement et les remplacer simplement par un opérateur **delete** à deux arguments.

   Si vous ne souhaitez pas mettre à jour votre code immédiatement, vous pouvez revenir à l’ancien comportement en utilisant l’option de compilateur `/Zc:sizedDealloc-`. Si vous utilisez cette option, les fonctions **delete** à deux arguments n’existent pas et ne provoquent pas de conflit avec votre opérateur **placement delete**.

- **Membres de données d’union**

   Les membres de données d'unions ne peuvent plus posséder de types de référence. Le code suivant se compile correctement dans Visual Studio 2013, mais génère une erreur dans Visual Studio 2015.

   ```cpp
    union U1 {
        const int i;
    };
    union U2 {
       int &i;
    };
    union U3 {
        struct {int &i;};
    };
   ```

   Le code précédent génère les erreurs suivantes :

   ```Output
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type
    test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type
   ```

   Pour résoudre ce problème, modifiez les types de référence en spécifiant un pointeur ou une valeur. La modification du type en pointeur nécessite des modifications dans le code qui utilise le champ union. La modification du code en valeur modifierait les données stockées dans l'union, ce qui affecte les autres champs dans la mesure où les champs dans les types d'union partagent la même mémoire. Selon la taille de la valeur, cela peut également modifier la taille de l'union.

- Les **unions anonymes**

   sont à présent plus conformes à la norme. Les versions précédentes du compilateur généraient un constructeur explicite et un destructeur pour les unions anonymes. Ceux-ci sont supprimés dans Visual Studio 2015.

   ```cpp
   struct S {
      S();
   };

   union {
      struct {
         S s;
      };
   } u; // C2280
   ```

   Le code précédent génère l’erreur suivante dans Visual Studio 2015 :

   ```cpp
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here
   ```

   Pour résoudre ce problème, fournissez vos propres définitions du constructeur et/ou du destructeur.

   ```cpp
    struct S {
       // Provide a default constructor by adding an empty function body.
       S() {}
    };

    union {
       struct {
          S s;
       };
    } u;
   ```

- **Unions avec structs anonymes**

   Pour se conformer à la norme, le comportement d'exécution a changé pour les membres de structures anonymes dans les unions. Le constructeur pour les membres de structure anonymes dans une union n'est plus implicitement appelé lors de la création d'une telle union. De plus, le destructeur pour les membres de structure anonymes dans une union n'est plus implicitement appelé quand l'union passe hors de portée. Considérons le code suivant, dans lequel une union U contient une structure anonyme contenant un membre qui est une structure nommée S possèdant un destructeur.

   ```cpp
    #include <stdio.h>
    struct S {
        S() { printf("Creating S\n"); }
        ~S(){ printf("Destroying S\n"); }
    };
    union U {
        struct {
        S s;
    };
        U() {}
        ~U(){}
    };

    void f()
    {
        U u;
        // Destructor implicitly called here.
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
   ```

   Dans Visual Studio 2013, le constructeur de S est appelé quand l’union est créée, et le destructeur de S est appelé quand la pile de la fonction f est nettoyée. Mais dans Visual Studio 2015, le constructeur et le destructeur ne sont pas appelés. Le compilateur émet un avertissement à propos de ce changement de comportement.

   ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
   ```

   Pour restaurer le comportement d'origine, nommez la structure anonyme. Le comportement d'exécution des structures non anonymes est le même, quelle que soit la version du compilateur.

   ```cpp
    #include <stdio.h>

    struct S {
        S() { printf("Creating S.\n"); }
        ~S() { printf("Destroying S\n"); }
    };
    union U {
        struct {
            S s;
        } namedStruct;
        U() {}
        ~U() {}
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
   ```

   Sinon, essayez de déplacer le code du constructeur et du destructeur dans de nouvelles fonctions et ajoutez des appels à ces fonctions à partir du constructeur et du destructeur pour l'union.

   ```cpp
    #include <stdio.h>

    struct S {
        void Create() { printf("Creating S.\n"); }
        void Destroy() { printf("Destroying S\n"); }
    };
    union U {
        struct {
            S s;
        };
        U() { s.Create();  }
        ~U() { s.Destroy(); }
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

    char s[1024];
    printf("Press any key.\n");
    gets_s(s);
    return 0;
    }
   ```

- **Résolution de modèle**

   Des modifications ont été apportées à la résolution de noms pour les modèles. En C++, quand vous envisagez des candidats pour la résolution d'un nom, il peut arriver qu'un ou plusieurs noms considérés comme des correspondances potentielles produisent une instanciation de modèle non valide. Ces instanciations non valides ne provoquent normalement pas d'erreurs du compilateur, un principe appelé SFINAE (Substitution Failure Is Not An Error).

   À présent, si le principe SFINAE exige que le compilateur instancie la spécialisation d'un modèle de classe, toutes les erreurs qui surviennent au cours de ce processus sont des erreurs du compilateur. Dans les versions précédentes, le compilateur ignore de telles erreurs. Considérons par exemple le code suivant :

   ```cpp
    #include <type_traits>

    template<typename T>
    struct S
    {
    S() = default;
    S(const S&);
    S(S&&);

    template<typename U, typename = typename std::enable_if<std::is_base_of<T, U>::value>::type>
    S(S<U>&&);
    };

    struct D;

    void f1()
    {
    S<D> s1;
        S<D> s2(s1);
    }

    struct B
    {
    };

    struct D : public B
    {
    };

    void f2()
    {
    S<D> s1;
        S<D> s2(s1);
    }
   ```

   Si vous effectuez une compilation avec le compilateur actuel, vous obtenez l'erreur suivante :

   ```Output
    type_traits(1110): error C2139: 'D': an undefined class is not allowed as an argument to compiler intrinsic type trait '__is_base_of'
    ..\t331.cpp(14): note: see declaration of 'D'
    ..\t331.cpp(10): note: see reference to class template instantiation 'std::is_base_of<T,U>' being compiled
            with
            [
                T=D,
                U=D
            ]
   ```

   La raison en est qu'au point de la première invocation de is_base_of, la classe 'D' n'a pas encore été définie.

   Dans ce cas, la correction proposée consiste à ne pas utiliser type traits tant que la classe n’a pas été définie. Si vous placez les définitions de B et D au début du fichier de code, l’erreur est résolue. Si les définitions sont dans des fichiers d'en-tête, vérifiez l'ordre des instructions include pour les fichiers d'en-tête afin de vous assurer que toutes les définitions de classe sont compilées avant l'utilisation des modèles problématiques.

- **Constructeurs de copie**

   Dans Visual Studio 2013 et Visual Studio 2015, le compilateur génère un constructeur de copie pour une classe, si celle-ci a un constructeur de déplacement défini par l’utilisateur mais aucun constructeur de copie personnalisé. Dans Dev14, ce constructeur de copie généré implicitement est également marqué « = delete ».

### <a name="VS_Update1"></a> Améliorations de la conformité dans Visual Studio 2015 Update 1

- **Classes de base virtuelles privées et héritage indirect**

   Les versions précédentes du compilateur autorisaient une classe dérivée à appeler des fonctions membres de ses classes de base `private virtual` *dérivées indirectement*. Cet ancien comportement était incorrect et non conforme à la norme C++. Le compilateur n’accepte plus de code écrit de cette façon. Il émet dans ce cas l’erreur du compilateur C2280.

   ```Output
    error C2280: 'void *S3::__delDtor(unsigned int)': attempting to reference a deleted function
   ```

   Exemple (avant)

   ```cpp
    class base
    {
    protected:
        base();
        ~base();
    };

    class middle: private virtual base {};class top: public virtual middle {};

    void destroy(top *p)
    {
        delete p;  //
    }
   ```

   Exemple (après)

   ```cpp
    class base;  // as above

    class middle: protected virtual base {};
    class top: public virtual middle {};

    void destroy(top *p)
    {
        delete p;
    }
   ```

  \- ou -

   ```cpp
    class base;  // as above

    class middle: private virtual base {};
    class top: public virtual middle, private virtual bottom {};

    void destroy(top *p)
    {
        delete p;
    }
   ```

- **Opérateurs new et delete surchargés**

   Avec les versions précédentes du compilateur, vous pouviez déclarer un **operator new** non membre et un **operator delete** non membre comme static, et vous pouviez les déclarer dans d’autres espaces de noms que l’espace de noms global.  Cet ancien comportement présentait un risque. En effet, il pouvait arriver que le programme n’appelle pas l’implémentation de l’opérateur **new** ou **delete** prévue par le programmeur, ce qui entraînait un comportement d’exécution incorrect sans générer d’avertissement. Le compilateur n’accepte plus de code écrit de cette façon. Au lieu de cela, il émet l’erreur du compilateur C2323.

   ```Output
    error C2323: 'operator new': non-member operator new or delete functions may not be declared static or in a namespace other than the global namespace.
   ```

   Exemple (avant)

   ```cpp
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323
   ```

   Exemple (après)

   ```cpp
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'
   ```

   De plus, bien que le compilateur ne donne pas de diagnostic spécifique, l’opérateur new inline est considéré comme incorrect.

- **Appel de 'operator *type*()' (conversion définie par l’utilisateur) sur des types autres que des types classe** Les versions précédentes du compilateur autorisaient l’appel de 'operator *type*()' sur des types autres que des types classe et ignoraient cet appel en silence. Cet ancien comportement créait un risque de génération de code incorrect en mode silencieux qui provoquait un comportement imprévisible au moment de l’exécution. Le compilateur n’accepte plus de code écrit de cette façon. Au lieu de cela, il émet l’erreur du compilateur C2228.

   ```Output
    error C2228: left of '.operator type' must have class/struct/union
   ```

   Exemple (avant)

   ```cpp
    typedef int index_t;

    void bounds_check(index_t index);

    void login(int column)
    {
        bounds_check(column.operator index_t());  // error C2228
    }
   ```

   Exemple (après)

   ```cpp
    typedef int index_t;

    void bounds_check(index_t index);

    void login(int column)
    {
         bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int'
    }
   ```

- **typename redondant dans les spécificateurs de type élaborés** Les versions précédentes du compilateur autorisaient **typename** dans les spécificateurs de type élaborés. Le code écrit de cette manière est sémantiquement incorrect. Le compilateur n’accepte plus de code écrit de cette façon. Au lieu de cela, il émet l’erreur du compilateur C3406.

   ```Output
    error C3406: 'typename' cannot be used in an elaborated type specifier
   ```

   Exemple (avant)

   ```cpp
    template <typename class T>
    class container;
   ```

   Exemple (après)

   ```cpp
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case
    class container;
   ```

- **Déduction de type des tableaux à partir d’une liste d’initialiseurs** Les versions précédentes du compilateur ne prenaient pas en charge la déduction de type des tableaux à partir d’une liste d’initialiseurs. Le compilateur prend désormais en charge cette forme de déduction de type. Ainsi, les appels à des modèles de fonctions à l’aide de listes d’initialiseurs peuvent maintenant être ambigus ou une surcharge autre que dans les versions précédentes du compilateur peut être choisie. Pour résoudre ces problèmes, le programme doit maintenant spécifier explicitement la surcharge prévue par le programmeur.

   Lorsque, à cause de ce nouveau comportement, la résolution de surcharge prend en compte un candidat supplémentaire qui est tout aussi efficace que le candidat historique, l’appel devient ambigu et le compilateur émet l’erreur C2668.

   ```Output
    error C2668: 'function' : ambiguous call to overloaded function.
   ```

   Exemple 1 : appel ambigu à une fonction surchargée (avant)

   ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...)
    template <typename... Args>
    void f(int, Args...);  //

    template <int N, typename... Args>
    void f(const int (&)[N], Args...);

    int main()
    {
        // The compiler now considers this call ambiguous, and issues a compiler error
        f({3});  error C2668: 'f' ambiguous call to overloaded function
    }
   ```

   Exemple 1 : appel ambigu à une fonction surchargée (après)

   ```cpp
    template <typename... Args>
    void f(int, Args...);  //

    template <int N, typename... Args>
    void f(const int (&)[N], Args...);

    int main()
    {
        // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it.
        f(3);
    }
   ```

   Lorsque, à cause de ce nouveau comportement, la résolution de surcharge prend en compte un candidat supplémentaire qui est une meilleure correspondance que le candidat historique, l’appel résout sans ambiguïté le nouveau candidat, ce qui provoque une modification du comportement du programme probablement différente de ce que le programmeur a prévu.

   Exemple 2 : modification de la résolution de surcharge (avant)

   ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...)
    struct S
    {
        int i;
        int j;
    };

    template <typename... Args>
    void f(S, Args...);

    template <int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // The compiler now resolves this call to f(const int (&)[N], Args...) instead
        f({1, 2});
    }
   ```

   Exemple 2 : modification de la résolution de surcharge (après)

   ```cpp
    struct S;  // as before

    template <typename... Args>
    void f(S, Args...);

    template <int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // To call f(S, Args...), perform an explicit cast to S on the initializer list.
        f(S{1, 2});
    }
   ```

- **Restauration des avertissements d’instruction switch**

   Une version précédente du compilateur supprimait les avertissements préexistants liés aux instructions **switch**. Ces avertissements ont été rétablis. Le compilateur émet désormais les avertissements restaurés, et les avertissements liés à des cas spécifiques (notamment le cas par défaut) sont désormais émis sur la ligne contenant le cas qui pose problème, plutôt que sur la dernière ligne de l’instruction switch. Comme ces avertissements ne sont plus émis sur les mêmes lignes qu’auparavant, les avertissements précédemment supprimés à l’aide de `#pragma warning(disable:####)` peuvent ne plus être supprimés comme prévu. Pour supprimer ces avertissements comme prévu, vous devrez peut-être déplacer la directive `#pragma warning(disable:####)` vers une ligne au-dessus du premier cas potentiellement incriminé. Voici les avertissements restaurés.

   ```Output
    warning C4060: switch statement contains no 'case' or 'default' labels
   ```

   ```Output
    warning C4061: enumerator 'bit1' in switch of enum 'flags' is not explicitly handled by a case label
   ```

   ```Output
    warning C4062: enumerator 'bit1' in switch of enum 'flags' is not handled
   ```

   ```Output
    warning C4063: case 'bit32' is not a valid value for switch of enum 'flags'
   ```

   ```Output
    warning C4064: switch of incomplete enum 'flags'
   ```

   ```Output
    warning C4065: switch statement contains 'default' but no 'case' labels
   ```

   ```Output
    warning C4808: case 'value' is not a valid value for switch condition of type 'bool'
   ```

   ```Output
    Warning C4809: switch statement has redundant 'default' label; all possible 'case' labels are given
   ```

   Exemple d’avertissement C4063 (avant)

   ```cpp
    class settings
    {
    public:
        enum flags
        {
            bit0 = 0x1,
            bit1 = 0x2,
            ...
        };
        ...
    };

    int main()
    {
        auto val = settings::bit1;

        switch (val)
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

        case settings::bit0 | settings::bit1:  // warning C4063
            break;
        }
    };
   ```

   Exemple d’avertissement C4063 (après)

   ```cpp
    class settings {...};  // as above

    int main()
    {
        // since C++11, use std::underlying_type to determine the underlying type of an enum
        typedef std::underlying_type<settings::flags>::type flags_t;

        auto val = settings::bit1;

        switch (static_cast<flags_t>(val))
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

        case settings::bit0 | settings::bit1:  // ok
            break;
        }
    };
   ```

   Des exemples des autres avertissements restaurés sont fournis dans leur documentation.

- **#include : utilisation du spécificateur de répertoire parent '..' dans le chemin** (concerne uniquement `/Wall` `/WX`)

   Les versions précédentes du compilateur ne détectaient pas l’utilisation du spécificateur de répertoire parent ’..’ dans le chemin d’accès des directives  `#include` . Le code écrit de cette manière est généralement conçu pour inclure des en-têtes qui existent en dehors du projet en utilisant de manière incorrecte des chemins d’accès relatifs au projet. Cet ancien comportement créait un risque que le programme puisse être compilé en incluant un fichier source différent de celui prévu par le programmeur, ou que ces chemins d’accès relatifs ne soient pas portables vers d’autres environnements de génération. Désormais, le compilateur détecte et informe le programmeur du code écrit de cette façon, et il émet un avertissement C4464 facultatif si cette fonctionnalité est activée.

   ```Output
    warning C4464: relative include path contains '..'
   ```

   Exemple (avant)

   ```cpp
    #include "..\headers\C4426.h"  // emits warning C4464
   ```

   Exemple (après)

   ```cpp
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories
   ```

   De plus, bien que le compilateur ne donne pas de diagnostic spécifique, nous vous recommandons également de ne pas utiliser le spécificateur de répertoire parent ".." pour spécifier les répertoires Include de votre projet.

- **#pragma optimize() s’étend au-delà de la fin du fichier d’en-tête** (affecte uniquement `/Wall` `/WX`)

   Les versions précédentes du compilateur ne détectaient pas les modifications apportées aux paramètres de l’indicateur d’optimisation qui échappent un fichier d’en-tête inclus dans une unité de traduction. Désormais, le compilateur détecte et informe le programmeur du code écrit de cette façon, et il émet un avertissement C4426 facultatif à l’emplacement du `#include`incriminé, si cette fonctionnalité est activée. Cet avertissement est émis uniquement si le modifications entrent en conflit avec les indicateurs d’optimisation définis par des arguments de ligne de commande au compilateur.

   ```Output
    warning C4426: optimization flags changed after including header, may be due to #pragma optimize()
   ```

   Exemple (avant)

   ```cpp
    // C4426.h
    #pragma optimize("g", off)
    ...
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"  // warning C4426
   ```

   Exemple (après)

   ```cpp
    // C4426.h
    #pragma optimize("g", off)
    ...
    #pragma optimize("", on)  // restores optimization flags set via command-line arguments
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"
   ```

- **Incompatibilité de #pragma warning(push)** et de **#pragma warning(pop)** (affecte uniquement `/Wall` `/WX`)

   Les versions précédentes du compilateur ne détectaient pas les associations des modifications d’état `#pragma warning(push)` aux modifications d’état `#pragma warning(pop)` dans un autre fichier source, qui sont rarement souhaitées. Cet ancien comportement créait un risque que le programme soit compilé avec un autre ensemble d’avertissements activé que celui prévu par le programmeur, ce qui pouvait provoquer un comportement incorrect en mode silencieux. Désormais, le compilateur détecte et informe le programmeur du code écrit de cette façon, et il émet un avertissement C5031 facultatif à l’emplacement du `#pragma warning(pop)` correspondant, si cette fonctionnalité est activée. Cet avertissement inclut une note faisant référence à l’emplacement du `#pragma warning(push)` correspondant.

   ```Output
    warning C5031: #pragma warning(pop): likely mismatch, popping warning state pushed in different file
   ```

   Exemple (avant)

   ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    ...
    #pragma warning(pop)  // pops a warning state not pushed in this source file
    ...
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling'
    ...
    #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031
    ...
   ```

   Exemple (après)

   ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)  // pops the warning state pushed in this source file
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    #pragma warning(push)  // pushes the warning state pushed in this source file
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order.
    ...
    #include "C5031_part2.h"
    ...
   ```

   Bien que rare, le code écrit de cette manière est parfois intentionnel. Le code écrit de cette manière est sensible aux modifications de l’ordre de `#include`. Dans la mesure du possible, nous conseillons que les fichiers de code source gèrent l’état d’avertissement de façon autonome.

- **#pragma warning(push) sans correspondance** (affecte uniquement `/Wall` `/WX`)

   Les versions précédentes du compilateur ne détectaient pas les modifications d’état `#pragma warning(push)` sans correspondance à la fin d’une unité de traduction. Désormais, le compilateur détecte le code écrit de cette façon et le notifie au programmeur. Il émet également un avertissement C5032 facultatif à l’emplacement du `#pragma warning(push)` sans correspondance, si cette fonctionnalité est activée. Cet avertissement est émis uniquement s’il n’y a aucune erreur de compilation dans l’unité de traduction.

   ```Output
    warning C5032: detected #pragma warning(push) with no corresponding #pragma warning(pop)
   ```

   Exemple (avant)

   ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5032.h ends without #pragma warning(pop)

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h
   ```

   Exemple (après)

   ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop) // matches #pragma warning (push) on line 1
    // C5032.h ends

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)
   ```

- **Des avertissements supplémentaires peuvent être émis à la suite du suivi d’état du #pragma warning amélioré**

   Les versions précédentes du compilateur ne suivaient pas les modifications de l’état d’avertissement `#pragma warning` assez bien pour émettre tous les avertissements prévus. Ce comportement créait un risque que certains avertissements soient supprimés dans des circonstances autres que celles prévues par le programmeur. Le compilateur effectue maintenant un suivi d’état de `#pragma warning` de manière plus complète, en particulier en ce qui concerne les changements d’état de `#pragma warning` dans les modèles. De plus, il émet éventuellement de nouveaux avertissements C5031 et C5032 destinés à aider le programmeur à détecter les utilisations involontaires de `#pragma warning(push)` et `#pragma warning(pop)`.

   Grâce à l’amélioration du suivi des changements d’état de `#pragma warning`, les avertissements qui étaient improprement supprimés ou ceux liés à des problèmes auparavant mal diagnostiqués peuvent désormais être émis.

- **Amélioration de l’identification du code inaccessible**

   Les modifications apportées à la bibliothèque standard C++ et la capacité améliorée à intégrer des appels de fonction par rapport aux versions précédentes du compilateur peuvent permettre au compilateur de prouver que du code est désormais inaccessible. Ce nouveau comportement peut provoquer des instances nouvelles et plus fréquentes de l’avertissement C4720.

   ```Output
    warning C4720: unreachable code
   ```

   Dans de nombreux cas, cet avertissement peut être émis uniquement lors de la compilation avec les optimisations activées, car les optimisations peuvent intégrer plus d’appels de fonction, supprimer le code redondant ou permettre de déterminer que du code est inaccessible. Nous avons constaté que de nouvelles instances de l’avertissement C4720 étaient fréquentes dans les blocs **try/catch**, en particulier en cas d’utilisation de [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True).

   Exemple (avant)

   ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch(...)
    {
        do_something();  // ok
    }
   ```

   Exemple (après)

   ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch(...)
    {
        do_something();  // warning C4702: unreachable code
    }
   ```

### <a name="VS_Update2"></a> Améliorations de la conformité dans Visual Studio 2015 Update 2

- **Des erreurs et avertissements supplémentaires peuvent être générés en raison de la prise en charge partielle de l’expression SFINAE.**

   Dans les versions précédentes du compilateur, certains types d’expressions au sein des spécificateurs **decltype** n’étaient pas analysés en raison de l’absence de prise en charge de l’expression SFINAE. Cet ancien comportement était incorrect et non conforme à la norme C++. À présent, le compilateur analyse ces expressions et offre une prise en charge partielle de l’expression SFINAE grâce à certaines améliorations récentes de la conformité. Par conséquent, le compilateur génère maintenant des avertissements et des erreurs détectés dans des expressions qui n’étaient pas analysées dans les versions précédentes du compilateur.

   Quand ce nouveau comportement analyse une expression **decltype** ayant un type qui n’a pas encore été déclaré, le compilateur génère l’erreur C2039.

   ```Output
    error C2039: 'type': is not a member of '`global namespace''
   ```

   Exemple 1 : utilisation d’un type non déclaré (avant)

   ```cpp
    struct s1
    {
      template <typename T>
      auto f() -> decltype(s2<T>::type::f());  // error C2039

      template<typename>
      struct s2 {};
    }
   ```

   Exemple 1 (après)

   ```cpp
    struct s1
    {
      template <typename>  // forward declare s2struct s2;

      template <typename T>
      auto f() -> decltype(s2<T>::type::f());

      template<typename>
      struct s2 {};
    }
   ```

   Quand ce nouveau comportement analyse une expression **decltype** dans laquelle il manque le mot clé **typename** obligatoire pour spécifier qu’un nom dépendant est un type, le compilateur génère l’avertissement C4346, ainsi que l’erreur C2923.

   ```Output
    warning C4346: 'S2<T>::Type': dependent name is not a type
   ```

   ```Output
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'
   ```

   Exemple 2 : le nom dépendant n’est pas un type (avant)

   ```cpp
    template <typename T>
    struct s1
    {
      typedef T type;
    };

    template <typename T>
    struct s2
    {
      typedef T type;
    };

    template <typename T>
    T declval();

    struct s
    {
      template <typename T>
      auto f(T t) -> decltype(t(declval<S1<S2<T>::type>::type>()));  // warning C4346, error C2923
    };
   ```

   Exemple 2 (après)

   ```cpp
    template <typename T> struct s1 {...};  // as above
    template <typename T> struct s2 {...};  // as above

    template <typename T>
    T declval();

    struct s
    {
      template <typename T>
      auto f(T t) -> decltype(t(declval<S1<typename S2<T>::type>::type>()));
    };
   ```

- `volatile` **Les variables membres n’autorisent pas les constructeurs et les opérateurs d’assignation définis implicitement** Dans les versions précédentes du compilateur, il était possible de générer automatiquement les constructeurs de copie/déplacement par défaut et les opérateurs d’assignation de copie/déplacement par défaut pour une classe ayant des variables membres **volatile**. Cet ancien comportement était incorrect et non conforme à la norme C++. À présent, le compilateur considère qu’une classe avec des variables de membre volatiles a des opérateurs de construction et d’assignation non triviaux, ce qui empêche la génération automatique des implémentations par défaut de ces opérateurs. Quand une telle classe est membre d’une union (ou d’une union anonyme au sein d’une classe), les constructeurs de copie/déplacement et les opérateurs d’assignation de copie/déplacement de l’union (ou de la classe contenant l’union anonyme) sont implicitement définis comme étant supprimés. Toute tentative de construction ou de copie de l’union (ou de la classe contenant l’union anonyme) sans avoir défini explicitement ces constructeurs ou opérateurs est considérée comme une erreur. Dans ce cas, le compilateur génère l’erreur C2280.

   ```Output
    error C2280: 'B::B(const B &)': attempting to reference a deleted function
   ```

   Exemple (avant)

   ```cpp
    struct A
    {
      volatile int i;
      volatile int j;
    };

    extern A* pa;

    struct B
    {
      union
      {
        A a;
        int i;
      };
    };

    B b1 {*pa};
    B b2 (b1);  // error C2280
   ```

   Exemple (après)

   ```cpp
    struct A
    {
      int i;int j;
    };

    extern volatile A* pa;

    A getA()  // returns an A instance copied from contents of pa
    {
      A a;
      a.i = pa->i;
      a.j = pa->j;
      return a;
    }

    struct B;  // as above

    B b1 {GetA()};
    B b2 (b1);  // error C2280
   ```

- **Les fonctions membres statiques ne prennent pas en charge les qualificateurs cv.**

   Dans les versions précédentes de Visual C++ 2015, les fonctions membres statiques pouvaient contenir des qualificateurs cv. Ce comportement est dû à une régression effectuée dans Visual C++ 2015 et dans Visual C++ 2015 Update 1. Le code écrit de cette manière est refusé dans Visual C++ 2013 et les versions antérieures de Visual C++. Le comportement de Visual C++ 2015 et de Visual C++ 2015 Update 1 est incorrect, et n’est pas conforme à la norme C++.  Visual Studio 2015 Update 2 refuse le code écrit de cette façon et génère l’erreur de compilateur C2511.

   ```Output
    error C2511: 'void A::func(void) const': overloaded member function not found in 'A'
   ```

   Exemple (avant)

   ```cpp
    struct A
    {
      static void func();
    };

    void A::func() const {}  // C2511
   ```

   Exemple (après)

   ```cpp
    struct A
    {
      static void func();
    };

    void A::func() {}  // removed const
   ```

- **La déclaration anticipée d’enum n’est pas autorisée dans le code WinRT** (concerne `/ZW` uniquement)

   Le code compilé pour WinRT (Windows Runtime) ne prend pas en charge la déclaration anticipée des types **enum**, comme dans le cas de la compilation du code C++ managé pour .Net Framework à l’aide du commutateur de compilateur `/clr`. Ce comportement garantit que la taille d’une énumération est toujours connue et qu’elle peut être projetée correctement vers le système de type WinRT. Le compilateur refuse le code écrit de cette façon et génère l’erreur de compilateur C2599 ainsi que l’erreur de compilateur C3197.

   ```Output
    error C2599: 'CustomEnum': the forward declaration of a WinRT enum is not allowed
   ```

   ```Output
    error C3197: 'public': can only be used in definitions
   ```

   Exemple (avant)

   ```cpp
    namespace A {
      public enum class CustomEnum: int32;  // forward declaration; error C2599, error C3197
    }

    namespace A {
      public enum class CustomEnum: int32
      {
        Value1
      };
    }

    public ref class Component sealed
    {
    public:
      CustomEnum f()
      {
        return CustomEnum::Value1;
      }
    };
   ```

   Exemple (après)

   ```cpp
              // forward declaration of CustomEnum removed
    namespace A {
      public enum class CustomEnum: int32
      {
        Value1
      };
    }

    public ref class Component sealed
    {
    public:
      CustomEnum f()
      {
        return CustomEnum::Value1;
      }
    };
   ```

- **L’opérateur non membre surchargé new et l’opérateur delete ne peuvent pas être déclarés inline**. Le niveau 1 (`/W1`) est activé par défaut.

   Les versions précédentes du compilateur ne génèrent pas d’avertissement quand les fonctions non membres **operator new** et **operator delete** sont déclarées inline. Le code écrit de cette manière est incorrect (aucun diagnostic nécessaire) et peut provoquer des problèmes de mémoire en raison de l’incompatibilité entre les opérateurs new et delete (en particulier, quand ils sont associés à la libération dimensionnée), qu’il est parfois difficile de diagnostiquer. À présent, le compilateur génère l’avertissement C4595 pour faciliter l’identification du code écrit de cette manière.

   ```Output
    warning C4595: 'operator new': non-member operator new or delete functions may not be declared inline
   ```

   Exemple (avant)

   ```cpp
    inline void* operator new(size_t sz)  // warning C4595
    {
      ...
    }
   ```

   Exemple (après)

   ```cpp
    void* operator new(size_t sz)  // removed inline
    {
      ...
    }
   ```

   Pour corriger le code écrit de cette manière, vous devrez peut-être déplacer les définitions d’opérateur du fichier d’en-tête vers le fichier source correspondant.

### <a name="VS_Update3"></a> Améliorations de la conformité dans Visual Studio 2015 Update 3

- **std::is_convertable détecte désormais l’auto-affectation** (bibliothèque standard) Les versions précédentes du trait de type `std::is_convertable` ne détectent pas correctement l’auto-affectation d’un type de classe quand son constructeur de copie est supprimé ou privé. Désormais, `std::is_convertable<>::value` a la valeur **false** (ce qui est correct) quand il est appliqué à un type de classe ayant un constructeur de copie supprimé ou privé.

   Aucun diagnostic du compilateur n’est associé à cette modification.

   Exemple

   ```cpp
    #include <type_traits>

    class X1
    {
    public:
        X1(const X1&) = delete;
    };

    class X2
    {
    private:
        X2(const X2&);
    };

    static_assert(std::is_convertible<X1&, X1>::value, "BOOM");static_assert(std::is_convertible<X2&, X2>::value, "BOOM");
   ```

   Dans les versions précédentes de Visual C++, les assertions statiques situées au bas de cet exemple parviennent à s’effectuer, car `std::is_convertable<>::value` a la valeur **true**, ce qui est incorrect. Désormais, `std::is_convertable<>::value` a la bonne valeur **false**, ce qui entraîne l’échec des assertions statiques.

- **Les constructeurs de copie et de déplacement ordinaires supprimés ou par défaut respectent les spécificateurs d’accès**

   Les versions précédentes du compilateur ne contrôlaient pas le spécificateur d’accès des constructeurs de copie et de déplacement ordinaires supprimés ou par défaut avant de les autoriser à être appelés. Cet ancien comportement était incorrect et non conforme à la norme C++. Dans certains cas, cet ancien comportement présentait le risque suivant : du code incorrect était généré sans avertissement, ce qui provoquait un comportement imprévisible au moment de l’exécution. Le compilateur vérifie désormais le spécificateur d’accès des constructeurs de copie et de déplacement ordinaires supprimés ou par défaut pour déterminer s’il peut être appelé et, dans le cas contraire, émet l’avertissement de compilateur C2248.

   ```Output
    error C2248: 'S::S' cannot access private member declared in class 'S'
   ```

   Exemple (avant)

   ```cpp
    class S {
    public:
       S() = default;
    private:
        S(const S&) = default;
    };

    void f(S);  // pass S by value

    int main()
    {
        S s;
        f(s);  // error C2248, can't invoke private copy constructor
    }
   ```

   Exemple (après)

   ```cpp
    class S {
    public:
       S() = default;
    private:
        S(const S&) = default;
    };

    void f(const S&);  // pass S by reference

    int main()
    {
        S s;
        f(s);
    }
   ```

- **Dépréciation de la prise en charge du code ATL avec attributs**. Le niveau 1 (`/W1`) est activé par défaut.

   Les versions précédentes du compilateur prenaient en charge le code ATL avec attributs. Comme phase suivante de la suppression de la prise en charge du code ATL avec attributs qui [est apparue dans Visual C++ 2008](https://msdn.microsoft.com/library/bb384632), le code ATL avec attributs a été déprécié. Le compilateur émet désormais l’avertissement C4467 pour faciliter l’identification de ce type de code déprécié.

   ```Output
    warning C4467: Usage of ATL attributes is deprecated
   ```

   Si vous souhaitez continuer à utiliser le code ATL avec attributs jusqu’à ce que la prise en charge soit supprimée du compilateur, vous pouvez désactiver cet avertissement en transmettant les arguments de ligne de commande `/Wv:18` ou `/wd4467` au compilateur, ou en ajoutant `#pragma warning(disable:4467)` à votre code source.

   Exemple 1 (avant)

   ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
   ```

   Exemple 1 (après)

   ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};
   ```

   Vous devez ou voulez parfois créer un fichier IDL pour éviter d’utiliser les attributs ATL dépréciés, comme dans l’exemple de code ci-dessous

   Exemple 2 (avant)

   ```cpp
    [emitidl];
    [module(name="Foo")];

    [object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
    __interface ICustom {
        HRESULT Custom([in] long l, [out, retval] long *pLong);
        [local] HRESULT CustomLocal([in] long l, [out, retval] long *pLong);
    };

    [coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
    class CFoo : public ICustom
    {
        // ...
    };
   ```

   Tout d’abord, créez le fichier *.idl ; le fichier vc140.idl généré peut être utilisé pour obtenir un fichier \*.idl contenant les interfaces et les annotations.

   Ajoutez ensuite une étape MIDL à votre génération pour vérifier que les définitions d’interface C++ sont générées.

   Exemple 2, IDL (après)

   ```cpp
    import "docobj.idl";

    [
        object,local,uuid(9e66a290-4365-11d2-a997-00c04fa37ddb)
    ]

    interface ICustom : IUnknown {
        HRESULT  Custom([in] long l, [out,retval] long *pLong);
        [local] HRESULT  CustomLocal([in] long l, [out,retval] long *pLong);
    };

    [ version(1.0), uuid(29079a2c-5f3f-3325-99a1-3ec9c40988bb) ]
    library Foo
    {
        importlib("stdole2.tlb");
        importlib("olepro32.dll");
            [
                version(1.0),
                appobject,uuid(9e66a294-4365-11d2-a997-00c04fa37ddb)
            ]

        coclass CFoo {
            interface ICustom;
        };
    }
   ```

   Utilisez ensuite ATL directement dans le fichier d’implémentation, comme dans l’exemple de code ci-dessous.

   Exemple 2, implémentation (après)

   ```cpp
    #include <idl.header.h>
    #include <atlbase.h>

    class ATL_NO_VTABLE CFooImpl :
        public ICustom,
        public ATL::CComObjectRootEx<CComMultiThreadModel>
    {
    public:
        BEGIN_COM_MAP(CFooImpl)
        COM_INTERFACE_ENTRY(ICustom)
        END_COM_MAP()
    };
   ```

- **Fichiers d’en-tête précompilés (PCH) et directives #include incompatibles** (concerne uniquement `/Wall` `/WX`)

   Les versions précédentes du compilateur acceptaient les directives `#include` incompatibles dans les fichiers sources entre les compilations `-Yc` et `-Yu` lors de l’utilisation de fichiers d’en-tête précompilés (PCH). Le code écrit de cette façon n’est plus accepté par le compilateur. Le compilateur émet désormais l’avertissement CC4598 pour faciliter l’identification des directives `#include` incompatibles lors de l’utilisation de fichiers PCH.

   ```Output
    warning C4598: 'b.h': included header file specified for Ycc.h at position 2 does not match Yuc.h at that position
   ```

   Exemple (avant) :

   X.cpp (-Ycc.h)

   ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
   ```

   Z.cpp (-Yuc.h)

   ```cpp
    #include "b.h"
    #include "a.h"  // mismatched order relative to X.cpp
    #include "c.h"
   ```

   Exemple (après)

   X.cpp (-Ycc.h)

   ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
   ```

   Z.cpp (-Yuc.h)

   ```cpp
    #include "a.h"
    #include "b.h" // matched order relative to X.cpp
    #include "c.h"
   ```

- **Fichiers d’en-tête précompilés (PCH) et répertoires include incompatibles** (concerne uniquement `/Wall` `/WX`)

   Les versions précédentes du compilateur acceptaient les arguments de ligne de commande des répertoires Include `-I` incompatibles passés au compilateur entre les compilations `-Yc` et `-Yu` lors de l’utilisation de fichiers d’en-tête précompilés (PCH). Le code écrit de cette façon n’est plus accepté par le compilateur.   Le compilateur émet désormais l’avertissement CC4599 pour faciliter l’identification des arguments de ligne de commande des répertoires Include (`-I`) incompatibles lors de l’utilisation de fichiers PCH.

   ```Output
    warning C4599: '-I..' : specified for Ycc.h at position 1 does not match Yuc.h at that position
   ```

   Exemple (avant)

   ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h Z.cpp
   ```

   Exemple (après)

   ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h -I.. Z.cpp
   ```

## <a name="whats-new-for-c-in-visual-studio-2013"></a>Nouveautés de C++ dans Visual Studio 2013

### <a name="improved-iso-cc-standards-support"></a>Prise en charge des normes ISO C/C++ améliorée

#### <a name="compiler"></a>Compilateur

MSVC prend en charge les fonctionnalités de langage ISO C++11 suivantes :

- Arguments template par défaut pour les modèles de fonction.
- Constructeurs effectuant une délégation
- Opérateurs de conversion explicite.
- Listes d'initialiseurs et initialisation uniforme.
- Littéraux de chaîne bruts.
- Modèles variadiques.
- Modèles d’alias.
- Fonctions supprimées.
- Initialiseurs de membres de données non statiques.
- Fonctions utilisées par défaut. \*
- Prend en charge les fonctionnalités de langage C99 suivantes :
- _Bool
- Littéraux composites.
- Initialiseurs désignés.
- Combinaison de déclarations et de code.
- La conversion de littéraux de chaîne en valeurs modifiables peut être interdite à l’aide de la nouvelle option de compilateur `/Zc:strictStrings`. En C++98, la conversion de littéraux de chaîne en `char*` (et de littéraux de chaîne étendus en `wchar_t*`) a été déconseillée. En C++11, la conversion a été entièrement supprimée. Bien que le compilateur puisse se conformer strictement à la norme, il propose à la place l'option `/Zc:strictStrings` qui vous permet de contrôler la conversion. L'option est désactivée par défaut. Notez que lorsque vous utilisez cette option en mode débogage, la bibliothèque STL n'est pas compilée.
- Casts de références rvalue/lvalue. Avec les références rvalue, C++11 peut clairement distinguer les valeurs lvalue des valeurs rvalue. Auparavant, le compilateur ne fournissait pas cette distinction dans certains scénarios de transtypage spécifiques. Une nouvelle option de compilateur, `/Zc:rvalueCast`, a été ajoutée pour rendre le compilateur conforme au document de travail sur le langage C++ (consultez la section 5.4, [expr.cast]/1). Le comportement par défaut lorsque cette option n'est pas spécifiée est le même que dans Visual Studio 2012.

> [!NOTE]
> Pour les fonctions par défaut, l’utilisation de =default pour demander des constructeurs de déplacement et des opérateurs d’assignation de déplacement entre membres n’est pas prise en charge.

### <a name="c99-libraries"></a>Bibliothèques C99

Des déclarations et des implémentations sont ajoutées pour les fonctionnalités manquantes dans ces en-têtes : math.h, ctype.h, wctype.h, stdio.h, stdlib.h et wchar.h. On trouve également les nouveaux en-têtes complex.h, stdbool.h, fenv.h et inttypes.h, ainsi que des implémentations pour toutes les fonctions déclarées dans ceux-ci. Il existe de nouveaux en-têtes de wrapper C++ (ccomplex, cfenv, cinttypes, ctgmath) et plusieurs autres sont mis à jour (ccomplex, cctype, clocale, cmath, cstdint, cstdio, cstring, cwchar et cwctype).

### <a name="standard-template-library"></a>Bibliothèque STL (Standard Template Library)

Prise en charge des opérateurs de conversion explicites C++11, des listes d'initialiseurs, des énumérations délimitées et des modèles variadiques.
Tous les conteneurs prennent désormais en charge les spécifications d'éléments affinées C++11.
Prise en charge des fonctionnalités C++14 suivantes :

- « Foncteurs d’opérateurs transparents » less<>, greater<>, plus<>, multiplies<>, et ainsi de suite.
- make_unique<T>(args...) et make_unique<T[]>(n)
- Fonctions non membres cbegin()/cend(), rbegin()/rend() et crbegin()/crend().
- \<atomic> a bénéficié de nombreuses améliorations en matière de performances.
- \<type_traits> a bénéficié de correctifs importants en matière de stabilisation et de code.

### <a name="breaking-changes"></a>Modifications avec rupture

Cette prise en charge améliorée des normes ISO C/C++ peut nécessiter des modifications du code existant afin qu’il soit conforme à C++11 et se compile correctement en Visual C++ dans Visual Studio 2013.

### <a name="visual-c-library-enhancements"></a>Améliorations de la bibliothèque Visual C++

- Le SDK C++ REST est ajouté. Il a une implémentation C++ moderne des services REST.
- La prise en charge de la texture C++ AMP a été améliorée. Cela inclut désormais la prise en charge des mipmaps et des nouveaux modes d'échantillonnage.
- Les tâches PPL prennent en charge plusieurs technologies de planification et le débogage asynchrone. De nouvelles API permettent de créer des tâches PPL pour les résultats normaux et les conditions d'exception.

### <a name="c-application-performance"></a>Performances de l'application C++

- Le vectoriseur automatique reconnaît et optimise désormais davantage de modèles C++ pour que votre code s’exécute plus rapidement.
- Améliorations de la qualité du code de la plateforme ARM et de la micro-architecture Atom.
- La convention d’appel __vectorcall est ajoutée. Passez les arguments de type vecteur en utilisant la convention d’appel __vectorcall pour utiliser des registres vectoriels.
- Nouvelles options de l’éditeur de liens. Les commutateurs `/Gw` (compilateur) et `/Gy` (assembleur) permettent aux optimisations de l'éditeur de liens de produire des fichiers binaires plus légers.
- Prise en charge de la mémoire partagée C++ AMP pour réduire ou éliminer la copie de données entre l’unité centrale et le GPU.

### <a name="profile-guided-optimization-pgo-enhancements"></a>Améliorations de l’optimisation guidée par profil (PGO)

- Améliorations des performances à partir d'une réduction du jeu de travail des applications optimisées à l'aide de l'optimisation guidée par profil.
- Nouvelle optimisation guidée par profil (PGO) du développement d’applications Windows Runtime.

### <a name="windows-runtime-app-development-support"></a>Prise en charge du développement d’applications Windows Runtime

- **Prise en charge des types encadrés dans les structs de valeur.**

   Vous pouvez désormais définir des types valeur à l’aide de champs qui peuvent avoir une valeur null, par exemple `IBox<int>^` par opposition à **int**. Cela signifie que les champs peuvent avoir une valeur ou être égaux à **nullptr**.

- **Informations plus détaillées sur l’exception.**

   C++/CX prend en charge le nouveau modèle d'erreurs Windows qui permet de capturer et de propager des informations d'exception enrichies sur l'interface binaire d'application (ABI) ; cela inclut les piles d'appels et les chaînes de messages personnalisées.

- **Object::ToString() est désormais virtuel.**

   Vous pouvez maintenant remplacer ToString dans les types de références Windows Runtime définis par l’utilisateur.

- **Prise en charge des API dépréciées.**

   Les API Windows Runtime publiques peuvent maintenant être marquées comme déconseillées. Par ailleurs, vous pouvez leur affecter un message personnalisé qui s'affiche sous forme d'avertissement de build et propose éventuellement des conseils de migration.

- **Améliorations du débogueur.**

   Prise en charge du débogage interop natif/JavaScript, diagnostic des exceptions Windows Runtime et débogage du code asynchrone (Windows Runtime et PPL).

> [!NOTE]
> En plus des fonctionnalités et améliorations propres au C++, décrites dans cette section, d’autres améliorations de Visual Studio peuvent également vous aider à écrire de meilleures applications Windows Runtime.

### <a name="diagnostics-enhancements"></a>Améliorations des diagnostics

- Améliorations du débogueur. Prise en charge du débogage asynchrone et du débogage Uniquement mon code.
- Catégories d’analyse du code. Vous pouvez maintenant afficher la sortie par catégorie de l'analyseur de code pour vous aider à identifier et à résoudre les erreurs de code.
- Diagnostics XAML. Vous pouvez maintenant diagnostiquer les problèmes de réponse de l'interface utilisateur et d'utilisation de la batterie dans votre XAML.
- Améliorations des graphiques et du débogage GPU.
- Capture et lecture à distance sur de véritables appareils.
- Débogage simultané de C++ AMP et de l'UC.
- Diagnostic amélioré du runtime C++ AMP.
- Débogage de trace de nuanceur de calcul HLSL.

### <a name="3-d-graphics-enhancements"></a>Améliorations des graphiques 3D

- Prise en charge du pipeline de contenu d’image pour le format DDS alpha prémultiplié.
- L’éditeur d’images utilise l’alpha prémultiplié en interne pour le rendu, ce qui évite d’effectuer le rendu d’artefacts tels que les halos sombres.
- Éditeurs d’images et de modèle. La création d’un filtre défini par l’utilisateur est maintenant prise en charge dans le concepteur Shader de l’éditeur d’images et de l’éditeur de modèle.

### <a name="ide-and-productivity"></a>Environnement IDE et productivité

**Mise en forme du code améliorée.** Vous pouvez appliquer d'autres paramètres de mise en forme à votre code C++. Avec ces paramètres, vous pouvez contrôler le positionnement sur une nouvelle ligne des accolades et des mots clés, la mise en retrait, l'espacement et le retour à la ligne. Le code est automatiquement mis en forme lorsque vous terminez des instructions et des blocs et lorsque que vous collez le code dans un fichier.

**Fin d’accolade.** Le code C++ complète désormais automatiquement les caractères fermants qui correspondent aux caractères ouvrants suivants :

- { (accolade)
- [ (crochet)
- ( (parenthèses)
- ' (guillemet simple)
- " (guillemet double)

**Autres fonctionnalités de saisie semi-automatique C++.**

- Ajoute le point-virgule pour les types de classe.
- Effectue une saisie semi-automatique des parenthèses pour les littéraux de chaîne bruts.
- Effectue une saisie semi-automatique des commentaires multilignes (/\* \*/)

**Rechercher toutes les références** résout maintenant automatiquement les références et les filtre en arrière-plan après avoir affiché la liste des correspondances textuelles.

**Filtrage de la liste des membres basé sur le contexte.** Les membres inaccessibles sont filtrés en étant exclus des listes de membres IntelliSense. Par exemple, les membres privés ne sont pas affichés dans la liste des membres, sauf si vous modifiez le code qui implémente le type. Tant que la liste des membres est ouverte, vous pouvez appuyer sur **Ctrl**+**J** pour supprimer un niveau de filtrage (s’applique uniquement à la fenêtre de la liste des membres actifs). Vous pouvez réappuyer sur **Ctrl**+**J** pour supprimer le filtrage textuel et afficher tous les membres.

**Défilement de l’aide sur les paramètres.** La signature de la fonction affichée dans l'info-bulle d'aide sur les paramètres change à présent selon le nombre de paramètres que vous avez réellement tapés, au lieu d'indiquer simplement une signature arbitraire non mise à jour en fonction du contexte actuel. L'aide relative aux paramètres fonctionne également correctement lorsqu'elle est affichée sur des fonctions imbriquées.

**Afficher ou masquer l’en-tête/le fichier de code.** Vous pouvez maintenant basculer entre un en-tête et son fichier de code correspondant à l'aide d'une commande du menu contextuel ou d'un raccourci clavier.

**Fenêtre Propriétés des projets C++ redimensionnable.**

**Génération automatique du code du gestionnaire d’événements en C++/CX et C++/CLI.**  Lorsque vous tapez du code pour ajouter un gestionnaire d'événements dans un fichier de code C++/CX ou C++/CLI, l'éditeur peut générer automatiquement l'instance de délégué et la définition du gestionnaire d'événements. Une fenêtre d'info-bulle apparaît lorsque le code de gestionnaire d'événements peut être généré automatiquement.

**Amélioration de la prise en charge DPI.** Le paramètre de prise en charge DPI pour les fichiers manifeste de l'application prend désormais en charge le paramètre « Reconnaissant les résolutions élevées par moniteur ».

**Basculement plus rapide entre les configurations.** Pour les grandes applications, le basculement entre les configurations, en particulier les opérations de basculement suivantes, s'exécute beaucoup plus rapidement.

**Efficacité du temps de build.** De nombreuses optimisations et l'utilisation de cœurs multiples rendent les builds plus rapides, en particulier pour les grands projets. Les builds incrémentielles des applications C++ possédant des références à C++ WinMD sont également plus rapides.

## <a name="whats-new-for-c-in-visual-studio-2012"></a>Nouveautés de C++ dans Visual Studio 2012

### <a name="improved-c11-standards-support"></a>Prise en charge améliorée des normes C++11

#### <a name="standard-template-library"></a>Bibliothèque STL (Standard Template Library)

- Prise en charge des nouveaux en-têtes STL : \<atomic>, \<chrono>, \<condition_variable>, \<filesystem>, \<future>, \<mutex>, \<ratio> et \<thread>.
- Pour optimiser l’utilisation des ressources mémoire, les conteneurs sont désormais plus petits. Par exemple, en mode de version x86 avec les paramètres par défaut, la taille de `std::vector` a été réduite de 16 octets dans Visual Studio 2010 à 12 octets dans Visual Studio 2012, et la taille de `std::map` a été réduit de 16 octets dans Visual Studio 2010 à 8 octets dans Visual Studio 2012.
- Comme c’est autorisé mais pas obligatoire dans la norme C++11, les itérateurs SCARY ont été implémentés.

#### <a name="other-c11-enhancements"></a>Autres améliorations C++11

- Boucles range-based for. Vous pouvez écrire des boucles plus fiables, que vous pouvez utiliser avec des tableaux, des conteneurs STL et des collections Windows Runtime sous la forme for (for-range-declaration : expression). Fait partie de la prise en charge du langage principal.
- Les expressions lambda sans état, qui sont des blocs de code commençant par une introduction d’expression lambda vide [] et ne capturant aucune variable locale, sont maintenant convertibles en pointeurs de fonction, comme l’exige la norme C++11.
- Prise en charge des énumérations délimitées. La clé Enum de la classe enum C++ est désormais prise en charge. Le code suivant montre comment cette clé Enum diffère du comportement enum précédent.

   ```cpp
  enum class Element { Hydrogen, Helium, Lithium, Beryllium };
  void func1(Element e);
  func1(Hydrogen); // error C2065: 'Hydrogen' : undeclared identifier
  func1(Element::Helium); // OK
   ```

### <a name="windows-runtime-app-development-support"></a>Prise en charge du développement d’applications Windows Runtime

- **Modèle d’interface utilisateur XAML native**. Pour les applications Windows Runtime, vous pouvez utiliser le nouveau modèle d’interface utilisateur XAML native.
- **Extensions de composant Visual C++** . Ces extensions simplifient la consommation d’objets Windows Runtime, qui sont indispensables pour les applications Windows Runtime. Pour plus d’informations, consultez [Feuille de route pour les applications Windows Runtime en C++](../windows/universal-windows-apps-cpp.md) et [Informations de référence du langage Visual C++ (C++/CX)](../cppcx/visual-c-language-reference-c-cx.md)
- **Jeux DirectX**. La nouvelle prise en charge de DirectX pour les applications Windows Runtime vous permet de développer des jeux captivants.
- **Interopérabilité XAML/DirectX**. Les applications Windows Runtime qui utilisent aussi bien XAML et DirectX interagissent désormais efficacement.
- **Développement de DLL de composant Windows Runtime**. Le développement de DLL de composant rend l’environnement Windows Runtime extensible.

### <a name="compiler-and-linker"></a>Compilateur et éditeur de liens

- **Vectoriseur automatique**. Le compilateur analyse les boucles de votre code et, dans la mesure du possible, génère des instructions qui utilisent les registres vectoriels et des instructions qui sont présentes dans tous les processeurs modernes. Cela accélère l’exécution des boucles. (Les instructions du processeur sont appelées « extensions Streaming SIMD » ou SSE, acronyme de Extensions Streaming SIMD). Il n’est pas nécessaire d’activer ou de demander cette optimisation, car elle est appliquée automatiquement.
- **Paralléliseur automatique**. Le compilateur peut analyser les boucles de votre code et générer des instructions qui répartissent les calculs sur plusieurs cœurs ou processeurs. Cela peut accélérer l’exécution des boucles. Vous devez demander cette optimisation, car elle n’est pas activée par défaut. Dans de nombreux cas, il est utile d’inclure `#pragma loop(hint_parallel(N))` dans votre code juste avant les boucles à paralléliser.
- Le vectoriseur automatique et le paralléliseur automatique peuvent fonctionner ensemble afin que les calculs soient répartis sur plusieurs cœurs et que le code sur chaque cœur utilise ses registres vectoriels.

### <a name="new-in-visual-studio-2012-update-1"></a>Nouveautés de Visual Studio 2012 Update 1

Ciblez Windows XP quand vous générez votre code C++.
Vous pouvez utiliser le compilateur et les bibliothèques Microsoft C++ pour cibler Windows XP et Windows Server 2003.

#### <a name="parallel-programming-support"></a>Prise en charge de la programmation parallèle

##### <a name="c-accelerated-massive-parallelism-amp"></a>C++ Accelerated Massive Parallelism (AMP)

C++ AMP accélère l’exécution de votre code C++ en profitant du matériel parallèle aux données qui est habituellement présent sous la forme d’un processeur graphique (GPU) sur une carte graphique discrète. Le modèle de programmation C++ AMP comprend des tableaux multidimensionnels, l’indexation, le transfert mémoire, la mosaïque et une bibliothèque de fonctions mathématiques. En utilisant des extensions de langage C++ AMP et des restrictions du compilateur, vous pouvez gérer le mode de déplacement des données de l’unité centrale vers le GPU, et inversement.

**Débogage.** L’expérience de débogage des applications qui utilisent C++ AMP pour cibler le GPU est similaire au débogage des autres applications C++. Cela inclut les nouveaux ajouts de débogage parallèle mentionnés précédemment.

**Profilage.** Il existe désormais une prise en charge du profilage pour l’activité du GPU qui est basée sur C++ AMP et sur d’autres modèles de programmation Direct3D.

#### <a name="general-parallel-programming-enhancements"></a>Améliorations de la programmation parallèle générale

Avec le matériel qui passe à des architectures multicœurs et à des architectures comprenant de nombreux cœurs, les développeurs ne peuvent plus compter sur des vitesses d’horloge sans cesse croissantes des cœurs uniques. La prise en charge de la programmation parallèle dans le runtime d’accès concurrentiel permet aux développeurs de tirer parti de ces nouvelles architectures.
Dans Visual Studio 2010, des bibliothèques de parallélisation C++ puissantes telles que la bibliothèque de modèles parallèles ont été introduites, ainsi que des fonctionnalités permettant de profiter de l’accès concurrentiel en exprimant des pipelines de flux de données sophistiqués. Dans Visual Studio 2012, ces bibliothèques ont été étendues afin d’améliorer les performances, de fournir davantage de contrôle et d’offrir une prise en charge plus importante des modèles parallèles dont les développeurs ont le plus besoin. L’étendue de l’offre inclut désormais :

- Un modèle de programmation basé sur les tâches complet qui prend en charge le comportement asynchrone et les continuations.
- Les algorithmes parallèles, qui prennent en charge le parallélisme de type duplication (fork)-jointure (parallel_for, parallel_for avec l’affinité, parallel_for_each, parallel_sort, parallel_reduce, parallel_transform).
- Les conteneurs d’accès concurrentiel sécurisé, qui fournissent des versions thread-safe des structures de données standard, comme priority_queue, queue, vector et map.
- La bibliothèque d’agents asynchrones, que les développeurs peuvent utiliser pour exprimer des pipelines de flux de données qui se décomposent naturellement en unités simultanées.
- Un planificateur personnalisable et un gestionnaire de ressources pour faciliter la composition lisse des modèles de cette liste.

##### <a name="general-parallel-debugging-enhancements"></a>Améliorations du débogage parallèle général

En plus de la fenêtre **Tâches parallèles** et de la fenêtre **Piles parallèles**, Visual Studio 2012 propose une nouvelle fenêtre **Espion parallèle** qui vous permet d’examiner les valeurs d’une expression dans tous les threads et processus, ainsi que de trier et de filtrer le résultat. Vous pouvez également utiliser vos propres visualiseurs pour développer la fenêtre, et vous pouvez tirer parti de la nouvelle prise en charge de plusieurs processus dans toutes les fenêtres Outil.

### <a name="ide"></a>IDE

**Prise en charge de modèles Visual Studio.** Vous pouvez maintenant utiliser la technologie de modèles Visual Studio pour créer des modèles d’élément et de projet C++.

**Chargement asynchrone des solutions.** Les projets sont désormais chargés de façon asynchrone (les éléments principaux de la solution en premier) pour vous permettre de commencer à travailler plus rapidement.

**Déploiement automatisé pour le débogage à distance.** Le déploiement de fichiers pour le débogage à distance en Visual C++ a été simplifié. L’option **Déployer** du menu contextuel du projet copie automatiquement sur l’ordinateur distant les fichiers spécifiés dans les propriétés de configuration du débogage. Il n’est plus nécessaire de copier manuellement les fichiers sur l’ordinateur distant.

**IntelliSense C++/CLI.** Désormais, C++/CLI prend totalement en charge IntelliSense. Les fonctionnalités IntelliSense, telles qu’Info express, Aide sur les paramètres, Liste des membres et Saisie semi-automatique, fonctionnent maintenant pour C++/CLI. De plus, les autres améliorations d’IntelliSense et d’IDE listées dans ce document fonctionnent également pour C++/CLI.

**Info-bulles IntelliSense améliorées** Les info-bulles Info express d’IntelliSense C++ affichent désormais des informations de style des commentaires de documentation XML plus détaillées. Si vous utilisez une API provenant d’une bibliothèque (par exemple, C++ AMP) qui contient des commentaires de documentation XML, l’info-bulle IntelliSense affiche davantage d’informations que la simple déclaration. De plus, si votre code contient des commentaires de documentation XML, les info-bulles IntelliSense affichent des informations plus détaillées.

**Constructions de code C++.** Le code squelette est disponible pour les constructions switch, if-else, for loop et d’autres constructions de code de base dans la liste déroulante Liste des membres. Sélectionnez un élément de code dans la liste pour l’insérer dans votre code, puis remplissez la logique exigée. Vous pouvez également créer vos propres éléments de code personnalisés à utiliser dans l’éditeur.

**Améliorations de la liste des membres.** La liste déroulante **Membres de la liste** s’affiche automatiquement au fur et à mesure que vous tapez du code dans l’éditeur de code. Les résultats sont filtrés pour que seuls les membres pertinents s’affichent à mesure que vous tapez. Dans la boîte de dialogue **Options**, sous **Éditeur de texte** > **C/C++**  > **Avancé**, vous pouvez contrôler le genre de logique de filtrage utilisé par la liste des membres.

**Colorisation sémantique.** Les types, les énumérations, les macros et les autres jetons C++ ont désormais une colorisation par défaut.

**Mise en surbrillance des références.** La sélection d’un symbole met désormais en surbrillance toutes les instances du symbole dans le fichier actuel. Appuyez sur **Ctrl**+**Maj**+**Haut** ou **Ctrl**+**Maj**+**Bas** pour vous déplacer entre les références en surbrillance. Vous pouvez désactiver cette fonctionnalité dans la boîte de dialogue **Options**, sous **Éditeur de texte** > **C/C++**  > **Avancé**.

### <a name="application-lifecycle-management-tools"></a>Outils de gestion du cycle de vie des applications

#### <a name="static-code-analysis"></a>Analyse statique du code

L’analyse statique de C++ a été mise à jour pour fournir des informations de contexte d’erreur plus détaillées, d’autres règles d’analyse et de meilleurs résultats d’analyse. Dans la nouvelle fenêtre Analyse du code, vous pouvez filtrer les messages par mot clé, par projet et par gravité. Quand vous sélectionnez un message dans la fenêtre, la ligne de code où le message a été déclenché est mise en surbrillance dans l’éditeur de code. Pour certains avertissements C++, le message liste les lignes sources qui indiquent le chemin d’exécution qui mène à l’avertissement. Les points de décision et les raisons du choix de ce chemin spécifique sont mis en surbrillance.
L’analyse du code est incluse dans la plupart des éditions de Visual Studio 2012. Dans les éditions Professional, Premium et Ultimate, toutes les règles sont incluses. Dans les éditions Express pour Windows 8 et Windows Phone, seuls les avertissements les plus critiques sont inclus. L’analyse du code n’est pas incluse dans l’édition Express pour le web.
Voici quelques autres améliorations de l’analyse du code :

- De nouveaux avertissements relatifs à l’accès concurrentiel vous aident à éviter les bogues d’accès concurrentiel en garantissant que vous utilisez les disciplines de verrouillage appropriées dans les programmes C/C++ multithread. L’analyseur détecte les conflits d’accès potentiels, les inversions d’ordre de verrou, les violations de contrat de verrouillage des appelants/appelés, les opérations de synchronisation incompatibles et d’autres bogues d’accès concurrentiel.
- Vous pouvez utiliser des ensembles de règles pour spécifier les règles C++ que vous voulez appliquer aux opérations d’analyse du code.
- Dans la fenêtre **Analyse du code**, vous pouvez insérer dans le code source un pragma qui supprime l’avertissement sélectionné.
- Vous pouvez améliorer la précision et l’exhaustivité de l’analyse statique du code à l’aide de la nouvelle version du langage d’annotation du code source (SAL) Microsoft pour décrire la manière dont une fonction utilise ses paramètres, les hypothèses qu’elle fait sur eux et les garanties qu’elle apporte quand elle est terminée.
- Prise en charge des projets C++ 64 bits.

#### <a name="updated-unit-test-framework"></a>Infrastructure de tests unitaires mise à jour

Utilisez la nouvelle infrastructure de tests unitaires C++ de Visual Studio pour écrire des tests unitaires C++. Ajoutez un nouveau projet de test unitaire à votre solution C++ existante en recherchant le modèle de projet de test unitaire C++ sous la catégorie Visual C++ dans la boîte de dialogue Nouveau projet. Commencez à écrire vos tests unitaires dans le stub de code TEST_METHOD généré dans le fichier Unittest1.cpp. Une fois le code de test écrit, générez la solution. Quand vous souhaitez exécuter les tests, ouvrez une fenêtre **Explorateur de tests unitaires** en choisissant **Affichage** > **Autres fenêtres** > **Explorateur de tests unitaires**, puis, dans le menu contextuel du cas de test approprié, choisissez **Exécuter le test sélectionné**. Une fois la série de tests terminée, vous pouvez consulter les résultats des tests et des informations supplémentaires sur la trace de la pile dans cette même fenêtre.

#### <a name="architecture-dependency-graphs"></a>Graphique de dépendance de l’architecture

Pour mieux comprendre votre code, vous pouvez maintenant générer des graphiques de dépendance pour le binaire, la classe, l’espace de noms et les fichiers include d’une solution. Dans la barre de menus, choisissez **Architecture** > **Générer un graphique de dépendance**, puis **Pour la solution** ou **Pour le fichier Include** afin de générer un graphique de dépendance. Une fois la génération du graphique effectuée, vous pouvez l’explorer en développant chaque nœud, découvrir les relations de dépendance en vous déplaçant entre les nœuds et parcourir le code source en choisissant **Afficher le contenu** dans le menu contextuel d’un nœud. Pour générer un graphique de dépendance des fichiers include, dans le menu contextuel d’un fichier de code source \*.cpp ou d’un fichier d’en-tête \*.h, choisissez **Générer le graphique des fichiers Include**.

#### <a name="architecture-explorer"></a>Navigateur de l'architecture

À l’aide du **Navigateur de l’architecture**, vous pouvez explorer les ressources de votre solution, de vos projets ou de vos fichiers C++. Dans la barre de menus, choisissez **Architecture** > **Fenêtres** > **Navigateur de l’architecture**. Vous pouvez sélectionner un nœud qui vous intéresse, par exemple **Affichage de classes**. Dans ce cas, le côté droit de la fenêtre Outil est développé pour afficher une liste d’espaces de noms. Si vous sélectionnez un espace de noms, une nouvelle colonne affiche la liste des classes, de structs et d’enums de cet espace de noms. Vous pouvez continuer à explorer ces ressources ou revenir à la colonne située à l’extrême gauche pour démarrer une autre requête. Consultez **Rechercher du code avec le navigateur de l’architecture**.

#### <a name="code-coverage"></a>Couverture du code

La couverture du code a été mise à jour pour instrumenter dynamiquement des binaires au moment de l’exécution. Cela réduit le surcroît de travail en termes de configuration et offre de meilleures performances. Vous pouvez également collecter des données de couverture du code à partir de tests unitaires pour les applications C++. Après avoir créé des tests unitaires C++, vous pouvez utiliser l’**Explorateur de tests unitaires** pour découvrir les tests de votre solution. Pour exécuter les tests unitaires et collecter les données de couverture du code correspondantes, dans l’**Explorateur de tests unitaires**, choisissez **Analyser la couverture du code**. Vous pouvez examiner les résultats de la couverture du code dans la fenêtre **Résultats de la couverture du code** : dans la barre de menus, choisissez **Test** > **Windows** > **Résultats de la couverture du code**.

## <a name="whats-new-for-c-in-visual-studio-2010"></a>Nouveautés de C++ dans Visual Studio 2010

### <a name="c-compiler-and-linker"></a>Compilateur et éditeur de liens C++

**Mot clé auto.** Le mot clé **auto** a une nouvelle finalité. Utilisez la signification par défaut du mot clé **auto** pour déclarer une variable dont le type est déduit de l’expression d’initialisation dans la déclaration de la variable. L’option de compilateur `/Zc:auto` appelle soit la nouvelle signification, soit la signification précédente du mot clé **auto**.

**Spécificateur de type decltype.** Le spécificateur de type **decltype** retourne le type de l’expression spécifiée. Utilisez le spécificateur de type **decltype** en combinaison avec le mot clé **auto** pour déclarer un type qui est soit complexe, soit connu uniquement du compilateur. Par exemple, utilisez cette combinaison pour déclarer une fonction de modèle dont le type de retour dépend des types de ses arguments template. Sinon, déclarez une fonction de modèle qui appelle une autre fonction, puis retourne le type de retour de la fonction appelée.

**Expressions lambda.** Les fonctions lambda ont un corps de fonction mais pas de nom. Les fonctions lambda combinent les meilleures caractéristiques des pointeurs de fonction et des objets de fonction. Utilisez une fonction lambda seule, comme un paramètre de fonction de modèle et non comme un objet de fonction, ou avec le mot clé **auto** pour déclarer une variable dont le type est celui d’une expression lambda.

**Référence rvalue.** Le déclarateur de référence rvalue (&&) déclare une référence à une valeur rvalue. Une référence rvalue vous permet d’utiliser la sémantique de mouvement et la transmission parfaite pour écrire des constructeurs, des fonctions et des modèles plus efficaces.

**Déclaration static_assert.** Une déclaration **static_assert** teste une assertion logicielle au moment de la compilation, contrairement à d’autres mécanismes d’assertion qui la testent au moment de l’exécution. Si l’assertion échoue, la compilation échoue aussi et un message d’erreur spécifié est émis.

**Mots clés nullptr et __nullptr.** MSVC vous permet d’utiliser le mot clé **nullptr** avec du code natif ou du code managé. Le mot clé **nullptr** indique qu’un descripteur d’objet, un pointeur intérieur ou un type de pointeur natif ne pointe pas vers un objet. Le compilateur interprète **nullptr** comme du code managé quand vous utilisez l’option de compilateur `/clr`, et comme du code natif quand vous n’utilisez pas l’option `/clr`.
Le mot clé **__nullptr** spécifique à Microsoft a la même signification que **nullptr**, mais il s’applique uniquement au code natif. Si vous compilez du code natif C/C++ à l’aide de l’option de compilateur `/clr`, le compilateur ne peut pas déterminer si le mot clé **nullptr** est un terme natif ou managé. Pour que vos intentions soient claires pour le compilateur, utilisez le mot clé nullptr pour spécifier le terme managé et **__nullptr** pour spécifier le terme natif.

**Option de compilateur /Zc:trigraphs.** Par défaut, la prise en charge des trigraphes est désactivée. Utilisez l’option de compilateur `/Zc:trigraphs` pour activer la prise en charge des trigraphes.
Un trigraphe se compose de deux points d’interrogation consécutifs (??) suivis d’un troisième caractère unique. Le compilateur remplace un trigraphe par le caractère de ponctuation correspondant. Par exemple, le compilateur remplace le trigraphe ??= par # (signe dièse). Utilisez des trigraphes dans les fichiers sources C qui utilisent un jeu de caractères ne contenant pas certains caractères de ponctuation.

**Nouvelle option d’optimisation guidée par profil.** PogoSafeMode est une nouvelle option d’optimisation guidée par profil qui vous permet de spécifier s’il faut utiliser le mode sans échec ou le mode rapide quand vous optimisez votre application. Le mode sans échec est thread-safe, mais il est plus lent que le mode rapide. Le mode rapide est le comportement par défaut.

**Nouvelle option du Common Language Runtime (CLR) /clr:nostdlib.** Une nouvelle option est ajoutée pour `/clr` (Compilation pour le Common Language Runtime). Si différentes versions des mêmes bibliothèques sont incluses, une erreur de compilation est émise. La nouvelle option vous permet d’exclure les bibliothèques CLR par défaut afin que votre programme puisse utiliser une version spécifiée.

**Nouvelle directive de pragma detect_mismatch.** La directive de pragma detect_mismatch vous permet de placer dans vos fichiers une balise qui est comparé à d’autres balises qui portent le même nom. S’il existe plusieurs valeurs pour le même nom, l’éditeur de liens génère une erreur.

**Intrinsèques XOP, intrinsèques FMA4 et intrinsèques LWP.** De nouvelles fonctions intrinsèques ont été ajoutées pour prendre en charge les intrinsèques XOP ajoutées pour Visual Studio 2010 SP1, les intrinsèques FMA4 ajoutées pour Visual Studio 2010 SP1 et les intrinsèques LWP ajoutées pour les technologies de processeur Visual Studio 2010 SP1. Utilisez __cpuid, __cpuidex pour déterminer quelles technologies de processeur sont prises en charge sur un ordinateur particulier.

### <a name="visual-studio-c-projects-and-the-build-system"></a>Projets Visual Studio C++ et le système de génération

**MSBuild.** Les projets et solutions Visual C++ sont désormais générés à l’aide de MSBuild.exe, qui remplace VCBuild.exe. MSBuild est le même outil de génération XML flexible et extensible que celui utilisé par les autres types de projets et langages Visual Studio. En raison de cette modification, les fichiers projet Visual Studio C++ utilisent désormais un format de fichier XML et portent l’extension de nom de fichier .vcxproj. Les fichiers projet Visual Studio C++ des versions antérieures de Visual Studio sont automatiquement convertis dans le nouveau format de fichier.

**Répertoires VC++.** Le paramètre Répertoires VC++ se trouve maintenant dans deux emplacements. Utilisez les pages de propriétés du projet pour définir des valeurs par projet pour les répertoires VC++. Utilisez le **Gestionnaire de propriétés** et une feuille de propriétés pour définir des valeurs globales par configuration pour les répertoires VC++.

**Dépendances entre projets.** Dans les versions antérieures, les dépendances définies entre les projets étaient stockées dans le fichier solution. Quand ces solutions sont converties dans le nouveau format de fichier projet, les dépendances sont converties en références entre projets. Cette modification peut affecter les applications, car les concepts de dépendances de solution et de références entre projets sont différents.

**Macros et variables d’environnement.** La nouvelle macro _ITERATOR_DEBUG_LEVEL appelle la prise en charge du débogage pour les itérateurs. Utilisez cette macro au lieu des anciennes macros _SECURE_SCL et _SECURE_SCL.

### <a name="visual-c-libraries"></a>Bibliothèques Visual C++

**Bibliothèques runtime d’accès concurrentiel.** L’infrastructure du runtime d’accès concurrentiel prend en charge les applications et les composants qui s’exécutent simultanément. Il s’agit de l’infrastructure de programmation d’applications simultanées en Visual C++. Pour prendre en charge la programmation d’applications simultanées, la bibliothèque de modèles parallèles (PPL) fournit des algorithmes et des conteneurs à usage général pour effectuer un parallélisme affiné. La bibliothèque d’agents asynchrones fournit un modèle de programmation reposant sur les acteurs et des interfaces de passage de messages pour le flux de données à granularité grossière et les tâches de traitement pipeline.

**Bibliothèque C++ standard.** La liste suivante décrit un grand nombre des modifications qui ont été apportées à la bibliothèque C++ Standard.

- La nouvelle fonctionnalité de référence rvalue du langage C++ a été utilisée pour implémenter la sémantique de mouvement et la transmission parfaite pour de nombreuses fonctions de la bibliothèque STL (Standard Template Library). La sémantique de mouvement et la transmission parfaite améliorent considérablement les performances des opérations qui allouent ou affectent des variables ou des paramètres.
- Les références rvalue sont également utilisées pour implémenter la nouvelle classe `unique_ptr`, qui est un type pointeur intelligent plus sécurisé que la classe `auto_ptr`. La classe `unique_ptr` peut être déplacée mais pas copiée. Elle implémente une sémantique de propriété stricte sans affecter la sécurité, et fonctionne bien avec les conteneurs qui prennent en charge les références rvalue. La classe `auto_ptr` est dépréciée.
- Quinze nouvelles fonctions, par exemple `find_if_not`, `copy_if` et `is_sorted`, ont été ajoutées à l’en-tête \<algorithm>.
- Dans l’en-tête \<memory>, la nouvelle fonction make_shared est un moyen pratique, fiable et efficace pour créer un pointeur partagé vers un objet au moment de la construction de l’objet.
- Les listes liées uniques sont prises en charge par l’en-tête \<forward_list>.
- Les nouvelles fonctions membres `cbegin`, `cend`, `crbegin` et `crend` fournissent un `const_iterator` qui se déplace vers l’avant ou vers l’arrière dans un conteneur.
- L’en-tête \<system_error> et les modèles associés prennent en charge le traitement des erreurs système de bas niveau. Les membres de la classe `exception_ptr` peuvent être utilisés pour transporter les exceptions entre les threads.
- L’en-tête \<codecvt> prend en charge la conversion de divers encodages de caractères Unicode en d’autres encodages.
- L’en-tête \<allocators> définit plusieurs modèles qui permettent d’allouer et de libérer des blocs de mémoire pour les conteneurs basés sur des nœuds.
- Il existe de nombreuses mises à jour de l’en-tête \<random>.

### <a name="microsoft-foundation-class-mfc-library"></a>Bibliothèques MFC (Microsoft Foundation Class)

**Fonctionnalités de Windows 7.** MFC prend en charge plusieurs fonctionnalités de Windows 7, par exemple l’interface utilisateur (IU) du ruban, la barre des tâches, les listes de raccourcis, les miniatures à onglets, les aperçus de miniatures, la barre de progression, la superposition d’image sur une icône et l’indexation de la recherche. Étant donné que MFC prend automatiquement en charge de nombreuses fonctionnalités de Windows 7, vous n’avez pas à modifier votre application existante. Pour prendre en charge d’autres fonctionnalités dans les nouvelles applications, utilisez l’Assistant Application MFC pour spécifier les fonctionnalités que vous souhaitez utiliser.

**Prise en charge de l’interaction tactile multipoint.** MFC prend en charge les applications qui ont une interface utilisateur tactile multipoint, par exemple les applications écrites pour le système d’exploitation Microsoft Surface. Une application tactile multipoint peut gérer les messages tactiles et les messages de geste Windows, qui sont des combinaisons de messages tactiles. Inscrivez simplement votre application pour les événements tactiles et de geste. Le système d’exploitation achemine alors les événements tactiles multipoint vers vos gestionnaires d’événements.

**Prise en charge de la haute résolution.** Par défaut, les applications MFC prennent désormais en charge la haute résolution. Si une application prend en charge la haute résolution, le système d’exploitation peut faire évoluer les fenêtres, le texte et d’autres éléments d’interface utilisateur avec la résolution d’écran actuelle. Ce signifie qu’une image mise à l’échelle est plus susceptible d’être correctement mise en forme, non pas tronquée ou sans aspect pixélisé.

**Gestionnaire de redémarrage.** Le Gestionnaire de redémarrage enregistre automatiquement les documents et redémarre votre application si elle se ferme ou redémarre de façon inattendue. Vous pouvez, par exemple, utiliser le Gestionnaire de redémarrage pour redémarrer votre application après sa fermeture provoquée par une mise à jour automatique. Pour plus d’informations sur la façon de configurer votre application afin d’utiliser le Gestionnaire de redémarrage, consultez **Guide pratique pour ajouter la prise en charge du Gestionnaire de redémarrage**.

**CTaskDialog.** Vous pouvez utiliser la classe `CTaskDialog` à la place de la boîte de message standard `AfxMessageBox`. La classe `CTaskDialog` affiche et rassemble plus d’informations que la boîte de message standard.

#### <a name="safeint-library"></a>Bibliothèque SafeInt

La nouvelle bibliothèque SafeInt exécute des opérations arithmétiques sécurisées qui prennent en compte le dépassement sur les entiers. Cette bibliothèque compare également différents types d’entiers.

#### <a name="new-active-template-library-atl-macros"></a>Nouvelles macros de la bibliothèque ATL (Active Template Library)

De nouvelles macros ont été ajoutées à la bibliothèque ATL pour développer les fonctionnalités de PROP_ENTRY_TYPE et de PROP_ENTRY_TYPE_EX. PROP_ENTRY_INTERFACE et PROP_ENTRY_INTERFACE_EX vous permettent d’ajouter une liste de CLSID valides. PROP_ENTRY_INTERFACE_CALLBACK et PROP_ENTRY_INTERFACE_CALLBACK_EX vous permettent de spécifier une fonction de rappel pour déterminer si un CLSID est valide.

#### <a name="analyze-warnings"></a>Avertissements /analyze

La plupart des avertissements `/analyze` (analyse du code d’entreprise) ont été supprimés des bibliothèques CRT (C Run-Time), MFC et ATL.

#### <a name="animation-and-d2d-support"></a>Prise en charge de l’animation et prise en charge D2D

MFC prend désormais en charge l’animation et les graphiques Direct2D. La bibliothèque MFC comprend plusieurs nouvelles classes et fonctions MFC pour prendre en charge cette fonctionnalité. Il existe également deux nouvelles procédures pas à pas montrant comment ajouter un objet D2D et un objet d’animation à un projet. Ces procédures pas à pas sont **Procédure pas à pas : ajout d’un objet D2D à un projet MFC (MFC)** et **Procédure pas à pas : ajout d’une animation à un projet MFC**.

### <a name="ide"></a>IDE

**Améliorations apportées à IntelliSense.** IntelliSense pour Visual C++ a été complètement repensé pour être plus rapide, plus précis et être en mesure de gérer des projets plus volumineux. Pour parvenir à cette amélioration, l’IDE fait une distinction entre la façon dont un développeur affiche et modifie le code source, et la façon dont l’IDE utilise le code source et les paramètres du projet pour créer une solution.
En raison de cette séparation des tâches, les fonctionnalités de navigation telles que l’**Affichage de classes** et la nouvelle boîte de dialogue **Naviguer vers** sont prises en charge par un système basé sur un nouveau fichier de base de données de bureau SQL Server (.sdf) qui remplace l’ancien fichier de navigation sans compilation (.ncb). Les fonctionnalités IntelliSense telles qu’Informations rapides, Saisie semi-automatique et Aide sur les paramètres analysent les unités de traduction uniquement en cas de besoin. Les fonctionnalités hybrides telles que la nouvelle fenêtre **Hiérarchie d’appels** utilisent une combinaison des fonctionnalités de navigation et IntelliSense.
Étant donné qu’IntelliSense traite uniquement les informations dont vous avez besoin à ce stade, l’IDE est plus réactif. De plus, étant donné que les informations sont plus à jour, les vues et les fenêtres de l’IDE sont plus précises. Enfin, comme l’infrastructure IDE étant mieux organisée, plus performante et plus scalable, elle peut gérer des projets plus volumineux.

**Amélioration des erreurs IntelliSense.** L’IDE détecte mieux les erreurs qui pourraient provoquer une perte d’IntelliSense et affiche des soulignements ondulés rouges en dessous. De plus, l’IDE signale les erreurs IntelliSense dans la fenêtre **Liste d’erreurs**. Pour afficher le code à l’origine du problème, double-cliquez sur l’erreur dans la fenêtre **Liste d’erreurs**.

**Fonctionnalité de saisie semi-automatique #include.** L’IDE prend en charge la complétion automatique pour le mot clé `#include`. Quand vous tapez `#include`, l’IDE crée une zone de liste déroulante des fichiers d’en-tête valides. Si vous poursuivez en tapant un nom de fichier, l’IDE filtre la liste en fonction de votre entrée. À tout moment, vous pouvez sélectionner dans la liste le fichier que vous souhaitez inclure. Cela vous permet d’inclure rapidement des fichiers sans connaître le nom exact des fichiers.

**Naviguer vers.** La boîte de dialogue **Naviguer vers** vous permet de rechercher tous les symboles et fichiers de votre projet qui correspondent à une chaîne spécifiée. Les résultats de la recherche sont immédiatement modifiés à mesure que vous tapez des caractères supplémentaires dans votre chaîne de recherche. Le champ de commentaires **Résultats** vous indique le nombre d’éléments trouvés et vous permet de décider s’il est nécessaire de limiter votre recherche. Les champs de commentaires **Genre/portée**, **Emplacement** et **Aperçu** vous permettent de lever l’ambiguïté entre les éléments qui ont des noms similaires. De plus, vous pouvez étendre cette fonctionnalité pour prendre en charge d’autres langages de programmation.

**Débogage parallèle et profilage.** Le débogueur Visual Studio a connaissance du runtime d’accès concurrentiel et vous aide à résoudre les problèmes liés aux applications de traitement en parallèle. Vous pouvez utiliser le nouvel outil profileur d’accès concurrentiel pour visualiser le comportement général de votre application. De plus, vous pouvez utiliser les nouvelles fenêtres Outil pour visualiser l’état des tâches et de leurs piles d’appels.

**Concepteur de ruban.** Le **Concepteur de ruban** est un éditeur graphique qui vous permet de créer et modifier une IU de ruban MFC. L’interface utilisateur finale du ruban est représentée par un fichier de ressources XML (.mfcribbon-ms). Pour les applications existantes, vous pouvez capturer votre IU de ruban actuelle en ajoutant temporairement quelques lignes de code, puis en appelant le **Concepteur de ruban**. Une fois le fichier de ressources de ruban créé, vous pouvez remplacer votre code d’interface utilisateur de ruban manuscrit par quelques instructions qui chargent la ressource du ruban.

**Hiérarchie d’appels.** La fenêtre **Hiérarchie d’appels** vous permet d’accéder à toutes les fonctions appelées par une fonction particulière, ou à toutes les fonctions qui appellent une fonction particulière.

### <a name="tools"></a>Outils

**Assistant Classe MFC.** Visual C++ 2010 rétablit l’outil Assistant classe MFC très apprécié. L’Assistant Classe MFC est un moyen pratique d’ajouter des classes, des messages et des variables à un projet sans avoir à modifier manuellement des ensembles de fichiers sources.

**Assistant Contrôle ATL.** L’Assistant Contrôle ATL ne remplit plus automatiquement le champ `ProgID`. Si un contrôle ATL n’a pas de `ProgID`, les autres outils risquent de ne pas fonctionner avec lui. La boîte de dialogue **Insérer un contrôle ActiveX** est un exemple d’outil pour lequel les contrôles doivent avoir un `ProgID`. Pour plus d’informations sur cette boîte de dialogue, consultez **Insérer un contrôle ActiveX, boîte de dialogue**.

### <a name="microsoft-macro-assembler-reference"></a>Référence de Microsoft Macro Assembler

L’ajout du type de données YMMWORD prend en charge les opérandes multimédias 256 bits inclus dans les instructions Advanced Vector Extensions (AVX) d’Intel.

## <a name="whats-new-for-c-in-visual-studio-2008"></a>Nouveautés de C++ dans Visual Studio 2008

### <a name="visual-c-integrated-development-environment-ide"></a>Environnement de développement intégré Visual C++ (IDE)

- Les boîtes de dialogue créées dans les applications ATL, MFC et Win32 respectent désormais les règles de style de Windows Vista. Quand vous créez un projet à l’aide de Visual Studio 2008, toutes les boîtes de dialogue que vous insérez dans votre application respecteront les règles de style de Windows Vista. Si vous recompilez un projet que vous avez créé avec une version antérieure de Visual Studio, les boîtes de dialogue existantes conservent le même aspect que précédemment. Pour plus d’informations sur la façon d’insérer des boîtes de dialogue dans votre application, consultez **Éditeur de boîtes de dialogue**.

- L’Assistant **Projet ATL** dispose désormais d’une option permettant d’inscrire les composants pour tous les utilisateurs. Depuis Visual Studio 2008, les composants et bibliothèques de types COM créés par l’Assistant **Projet ATL** sont inscrits dans le nœud HKEY_CURRENT_USER du Registre, sauf si vous sélectionnez **Inscrire le composant pour tous les utilisateurs**.
- L’Assistant **Projet ATL** ne fournit plus d’option permettant de créer des projets ATL avec attributs. Depuis Visual Studio 2008, l’**Assistant Projet ATL** ne dispose plus de l’option permettant de changer l’état avec attribut d’un nouveau projet. Tous les nouveaux projets ATL que l’Assistant crée sont désormais sans attributs.
- L’écriture dans le Registre peut être redirigée. Avec l’introduction de Windows Vista, l’écriture dans certaines zones du Registre exige qu’un programme s’exécute en mode élevé. Il n’est pas souhaitable de toujours exécuter Visual Studio en mode élevé. La redirection par utilisateur redirige automatiquement les écritures dans le Registre de HKEY_CLASSES_ROOT vers HKEY_CURRENT_USER sans aucun changement de la programmation.
- Le **Concepteur de classes** offre désormais une prise en charge limitée du code C++ natif. Dans les versions antérieures de Visual Studio, le **Concepteur de classes** fonctionnait uniquement avec Visual C# et Visual Basic. Les utilisateurs C++ peuvent désormais utiliser le **Concepteur de classes**, mais uniquement en mode lecture seule. Pour plus d’informations sur l’utilisation du **Concepteur de classes** en C++, consultez **Utilisation du code Visual C++ dans le Concepteur de classes**.
- L’Assistant Projet ne permet plus de créer un projet SQL Server en C++. À partir de Visual Studio 2008, le nouvel Assistant Projet ne permet pas de créer un projet SQL Server en C++. Les projets SQL Server créés à l’aide d’une version antérieure de Visual Studio seront cependant compilés et fonctionneront toujours correctement.

### <a name="visual-c-libraries"></a>Bibliothèques Visual C++

#### <a name="general"></a>Général

- Les applications peuvent être liées à des versions spécifiques des bibliothèques Visual C++. Parfois, une application dépend des mises à jour qui ont été effectuées aux bibliothèques Visual C++ après la mise sur le marché d’une version. Dans ce cas, l’exécution de l’application sur un ordinateur disposant de versions antérieures des bibliothèques permettre entraîner un comportement inattendu. Vous pouvez maintenant lier une application à une version spécifique des bibliothèques afin qu’elle ne soit pas exécutée sur un ordinateur disposant d’une version antérieure de celles-ci.

#### <a name="stlclr-library"></a>STL/CLR, bibliothèque

- Visual C++ inclut désormais la bibliothèque STL/CLR. La bibliothèque STL/CLR est un package de la bibliothèque STL (Standard Template Library), partie de la bibliothèque C++ standard, à utiliser avec C++ et le CLR (Common Language Runtime) du .NET Framework. Avec STL/CLR, vous pouvez maintenant utiliser tous les conteneurs, itérateurs et algorithmes de la bibliothèque STL dans un environnement managé.

#### <a name="mfc-library"></a>Bibliothèque MFC

- Windows Vista prend en charge les contrôles communs. Plus de 150 méthodes dans 18 classes nouvelles ou existantes ont été ajoutées pour prendre en charge les fonctionnalités de Windows Vista, ou pour améliorer les fonctionnalités dans les classes MFC actuelles.
- La nouvelle classe `CNetAddressCtrl` permet d’entrer et de valider les adresses IPv4 et IPv6, ou les noms DNS.
- La nouvelle classe `CPagerCtrl` simplifie l’utilisation du contrôle pager Windows.
- La nouvelle classe `CSplitButton` simplifie l’utilisation du contrôle Splitbutton Windows pour sélectionner une valeur par défaut ou une action facultative.

#### <a name="c-support-library"></a>bibliothèque de prise en charge C++

- C++ introduit la bibliothèque de marshaling. La bibliothèque de marshaling fournit un moyen simple et optimisé de marshaler des données entre des environnements natifs et managés. La bibliothèque est une alternative à des approches moins efficaces et plus complexes telles que l’utilisation de PInvoke. Pour plus d’informations, consultez **Vue d’ensemble du marshaling dans C++** .

#### <a name="atl-server"></a>ATL Server

- ATL Server est publié comme un projet source partagé.
- La plus grande partie du code base ATL Server a été publié comme projet source partagé sur CodePlex et n’est pas installé dans le cadre de Visual Studio 2008. Plusieurs fichiers associés à ATL Server ne font plus partie de Visual Studio. Pour obtenir la liste des fichiers supprimés, consultez **Fichiers de serveur ATL supprimés**.
- Les classes d’encodage et de décodage de données d’atlenc.h ainsi que les fonctions et classes utilitaires d’atlutil.h et d’atlpath.h font désormais partie de la bibliothèque ATL.
- Microsoft continuera à prendre en charge les versions d’ATL Server qui sont incluses dans les versions précédentes de Visual Studio tant que ces versions de Visual Studio seront prises en charge. CodePlex poursuivra le développement du code ATL Server comme un projet communautaire. Microsoft ne prend pas en charge une version CodePlex d’ATL Server.

### <a name="visual-c-compiler-and-linker"></a>Compilateur et éditeur de liens Visual C++

#### <a name="compiler-changes"></a>Changements du compilateur

- Le compilateur prend en charge les builds incrémentielles managées. Quand vous spécifiez cette option, le compilateur ne recompile pas le code en cas de modification d’un assembly référencé. Au lieu de cela, il effectue une build incrémentielle. Les fichiers sont recompilés uniquement si les changements affectent le code dépendant.
- Les attributs liés à ATL Server ne sont plus pris en charge. Le compilateur ne prend plus en charge plusieurs attributs qui étaient directement liés à ATL Server. Pour obtenir la liste complète des attributs supprimés, consultez Changements importants.
- Le compilateur prend en charge la microarchitecture Intel Core. Le compilateur contient le paramétrage pour la microarchitecture Intel Core pendant la génération du code. Par défaut, ce paramétrage est activé et ne peut pas être désactivé car il sert également aux processeurs Pentium 4 et à d’autres processeurs.
- Les intrinsèques prennent en charge les processeurs Intel et AMD plus récents. Plusieurs nouvelles instructions intrinsèques prennent en charge les fonctionnalités supérieures de processeurs Intel et AMD plus récents. Pour plus d’informations sur les nouveaux intrinsèques, consultez **Instructions SSE 3 (extensions Streaming SIMD 3 supplémentaires)** , **Instructions SSE 4 (extensions Streaming SIMD 4)** , **Intrinsèques de manipulation de bits avancés et SSE4A**, **Intrinsèques AES**, **_mm_clmulepi64_si128** et **__rdtscp**.
- La fonction `__cpuid` a été mise à jour. Les fonctions `__cpuid` et `__cpuidex` prennent désormais en charge plusieurs nouvelles fonctionnalités issues des dernières révisions des processeurs Intel et AMD. L’intrinsèque `__cpuidex` est nouveau et collecte davantage d’informations sur les processeurs récents.
- L’option de compilateur `/MP` réduit la durée de génération totale. L’option `/MP` peut réduire considérablement la durée totale de compilation de plusieurs fichiers sources en créant plusieurs processus qui compilent les fichiers simultanément. Cette option est particulièrement utile sur les ordinateurs qui prennent en charge l’hyperthreading, plusieurs processeurs ou plusieurs cœurs.
- L’option de compilateur `/Wp64` et le mot clé **__w64** sont dépréciés. L’option de compilateur `/Wp64` et le mot clé **__w64**, qui détectent les problèmes de portabilité 64 bits, sont dépréciés. Ils vont être supprimés dans une prochaine version du compilateur. Au lieu de cette option de compilateur et du mot clé, utilisez un MSVC qui cible une plateforme 64 bits.
- `/Qfast_transcendentals` génère du code inline pour les fonctions transcendantes.
- `/Qimprecise_fwaits` supprime les commandes fwait internes aux blocs try quand vous utilisez l’option de compilateur `/fp:except`.

### <a name="linker-changes"></a>Changements de l’éditeur de liens

- Les informations de contrôle de compte d’utilisateur sont maintenant incorporées dans des fichiers manifeste pour les exécutables par l’éditeur de liens Visual C++ (link.exe). Cette fonction est activée par défaut. Pour plus d’informations sur la manière de désactiver cette fonctionnalité ou de modifier le comportement par défaut, consultez `/MANIFESTUAC` (Incorporer des informations sur le contrôle de compte d’utilisateur dans le manifeste).
- L’éditeur de liens dispose désormais de l’option `/DYNAMICBASE` pour activer la fonctionnalité de randomisation du format d’espace d’adressage de Windows Vista. Cette option modifie l’en-tête d’un exécutable pour indiquer si l’application doit être rebasée de façon aléatoire au moment du chargement.

## <a name="whats-new-for-c-in-visual-studio-2005"></a>Nouveautés de C++ dans Visual Studio 2005

Les fonctionnalités suivantes étaient nouvelles dans Visual C++ 2005 Service Pack 1 :

### <a name="intrinsics-for-x86-and-x64"></a>Intrinsèques pour x86 et x64

- __halt
- __lidt
- __nop
- __readcr8
- __sidt
- __svm_clgi
- __svm_invlpga
- __svm_skinit
- __svm_stgi
- __svm_vmload
- __svm_vmrun
- __svm_vmsave
- __ud2
- __vmx_off
- __vmx_vmptrst
- __writecr8

### <a name="intrinsics-for-x64-only"></a>Intrinsèques pour x64 uniquement

- __vmx_on
- __vmx_vmclear
- __vmx_vmlaunch
- __vmx_vmptrld
- __vmx_vmread
- __vmx_vmresume
- __vmx_vmwrite

### <a name="new-language-keywords"></a>Nouveaux mots clés de langage

__sptr, __uptr

### <a name="new-compiler-features"></a>Nouvelles fonctionnalités du compilateur

Des changements importants ont été apportés au compilateur dans cette version.

- Compilateurs croisés et natifs 64 bits.
- L’option de compilateur `/analyze` (analyse du code d’entreprise) a été ajoutée.
- L’option de compilateur `/bigobj` a été ajoutée.
- `/clr:pure`, `/clr:safe` et `/clr:oldSyntax` ont été ajoutés. (Déconseillée ultérieurement dans Visual Studio 2015 et supprimée dans Visual Studio 2017.)
- Options de compilateur dépréciées : plusieurs options de compilateur ont été dépréciées dans cette version. Pour plus d’informations, consultez **Options de compilateur dépréciées**.
- La double conversion de code dans le code `/clr` est réduite. Pour plus d’informations, consultez **Double conversion de code (thunking) (C++)** .
- L’option `/EH` (Modèle de prise en charge des exceptions) ou `/EHs` ne peut plus être utilisée pour intercepter une exception levée par un autre élément qu’une clause throw. Utilisez `/EHa`.
- L’option de compilateur `/errorReport` (Signaler les erreurs internes du compilateur) a été ajoutée.
- L’option de compilateur `/favor` (Optimisation pour 64) a été ajoutée.
- L’option de compilateur `/FA`, `/Fa` (Fichier listing) a été ajoutée.
- L’option de compilateur `/FC` (Chemin complet du fichier de code source dans les diagnostics) a été ajoutée.
- L’option de compilateur `/fp` (Spécifier le comportement de virgule flottante) a été ajoutée.
- L’option de compilateur `/G` (Optimiser pour le processeur) a été ajoutée.
- L’option de compilateur `/G` (Optimiser pour le processeur) a été ajoutée.
- Les options de compilateur `/G3`, `/G4`, `/G5`, `/G6`, `/G7` et `/GB` ont été supprimées. Le compilateur utilise désormais un « modèle mixte » qui tente de créer le meilleur fichier de sortie pour toutes les architectures.
- La fonction `/Gf` a été supprimée. Utilisez `/GF` (Supprimer les doublons) à la place.
- `/GL` (Optimisation de l’ensemble du programme) est désormais compatible avec `/CLRHEADER`.
- `/GR` est désormais activé par défaut.
- `/GS` (Vérification de la sécurité de la mémoire tampon) fournit désormais une protection de sécurité pour les paramètres de pointeur vulnérables. `/GS` est désormais activé par défaut. Désormais, `/GS` fonctionne également sur les fonctions compilées en MSIL avec `/clr` (Compilation pour le Common Language Runtime).
- L’option de compilateur `/homeparams` (Copier les paramètres des registres vers la pile) a été ajoutée.
- L’option de compilateur `/hotpatch` (Créer une image corrigeable en mémoire) a été ajoutée.
- Les heuristiques de fonctions inline ont été mises à jour. Pour plus d’informations, consultez **inline**, **__inline**, **__forceinline** et **inline_depth**.
- De nombreuses nouvelles fonctions intrinsèques ont été ajoutées, et de nombreux intrinsèques précédemment non documentés sont maintenant documentée.
- Par défaut, tout appel à new qui échoue lèvera une exception.
- Les options de compilateur `/ML` et `/MLd` ont été supprimées. Visual C++ ne prend plus en charge les bibliothèques CRT monothread liées de manière statique.
- Le compilateur implémentait l’optimisation de la valeur de retour nommée, qui est activée quand vous compilez avec `/O1`, `/O2` (Réduire la taille, augmenter la vitesse), `/Og` (Optimisations globales) et `/Ox` (Optimisation complète).
- L’option de compilateur `/Oa` a été supprimée mais elle est ignorée sans générer d’avertissement. Utilisez les modificateurs `noalias` ou `restrict__declspec` pour spécifier la façon dont le compilateur crée les alias.
- L’option de compilateur `/Op` a été supprimée. Utilisez `/fp` (Spécifier le comportement de virgule flottante) à la place.
- OpenMP est maintenant pris en charge par Visual C++.
- L’option de compilateur `/openmp` (Activer la prise en charge OpenMP 2.0) a été ajoutée.
- L’option de compilateur `/Ow` a été supprimée, mais elle est ignorée sans générer d’avertissement. Utilisez les modificateurs `noalias` ou `restrict__declspec` pour spécifier la façon dont le compilateur crée les alias.

### <a name="profile-guided-optimizations"></a>Optimisations guidées par profil

- La fonction `/QI0f` a été supprimée.
- `/QIfdiv` a été supprimé.
- L’option de compilateur `/QIPF_B` (Errata pour l’exécution pas à pas UC B) a été ajoutée.
- L’option de compilateur `/QIPF_C` (Errata pour l’exécution pas à pas UC C) a été ajoutée.
- L’option de compilateur `/QIPF_fr32` (Ne pas utiliser les 96 registres de virgule flottante supérieurs) a été ajoutée.
- L’option de compilateur `/QIPF_noPIC` (Générer du code dépendant de la position) a été ajoutée.
- L’option de compilateur `/QIPF_restrict_plabels` (Supposer qu’aucune fonction n’a été créée au moment de l’exécution) a été ajoutée.

### <a name="unicode-support-in-the-compiler-and-linker"></a>Prise en charge Unicode dans le compilateur et l'éditeur de liens

- `/vd` (Désactiver les déplacements de construction) vous permet désormais d’utiliser l’opérateur dynamic_cast sur un objet en cours de construction (/vd2)
- L’option de compilateur `/YX` a été supprimée. Utilisez `/Yc` (Créer un fichier d’en-tête précompilé) ou `/Yu` (Utiliser un fichier d’en-tête précompilé) à la place. Si vous supprimez `/YX` de vos configurations de build sans le remplacer, cela peut produire des builds plus rapides.
- `/Zc:forScope` est désormais activé par défaut.
- `/Zc:wchar_t` est désormais activé par défaut.
- L’option de compilateur `/Zd` a été supprimée. Les informations de débogage uniquement des numéros de ligne ne sont plus prises en charge. Utilisez `/Zi` à la place. (Pour plus d’informations, consultez **/Z7, /Zi, /ZI (Format des informations de débogage)** ).
- `/Zg` est désormais valide uniquement sur les fichiers de code source C, et non sur les fichiers de code source C++.
- L’option de compilateur `/Zx` (Déboguer le code Itanium optimisé) a été ajoutée.

### <a name="new-language-features"></a>Nouvelles fonctionnalités de langage

- L’attribut attribute est désormais déprécié.
- Le modificateur `appdomain__declspec` a été ajouté.
- La convention d’appel `__clrcall` a été ajoutée.
- Le modificateur **declspec** (C++) déprécié vous permet désormais de spécifier une chaîne qui s’affiche au moment de la compilation, quand un utilisateur tente d’accéder à une classe ou une fonction dépréciée.
- L’opérateur **dynamic_cast** comporte des changements importants.
- Les enums natifs vous permettent désormais de spécifier le type sous-jacent.
- Le modificateur `jitintrinsicdeclspec` a été ajouté.
- Le modificateur `noaliasdeclspec` a été ajouté.
- Le modificateur `process__declspec` a été ajouté.
- **abstract**, **override** et **sealed** sont valides pour les compilations natives.
- Le mot clé **__restrict** a été ajouté.
- Le modificateur `restrictdeclspec` a été ajouté.
- **__thiscall** est désormais un mot clé.
- Le mot clé **__unaligned** est désormais documenté.
- Le comportement de **volatile** (C++) a été mis à jour par rapport aux optimisations.

### <a name="new-preprocessor-features"></a>Nouvelles fonctionnalités du préprocesseur

- La macro prédéfinie de __CLR_VER a été ajoutée.
- Le pragma comment (C/C++) accepte désormais `/MANIFESTDEPENDENCY` comme commentaire d’éditeur de liens. L’option exestr pour commenter est désormais dépréciée.
- L’attribut `embedded_idl` (directive `#import`) accepte désormais un paramètre optionnel.
- `fenv_access` pragma
- `float_control` pragma
- `fp_contract` pragma
- Les variables globales ne seront pas initialisées dans l’ordre où elles sont déclarées si vous avez des variables globales dans le pragma managed, unmanaged et dans les sections non gérées. Il s’agit d’un changement important potentiels si, par exemple, une variable globale non managée est initialisée avec une variable globale managée, et qu’un objet managé entièrement construit est exigé.
- Les sections spécifiées avec init_seg sont désormais en lecture seule, et pas en lecture/écriture comme dans les versions précédentes.
- La valeur par défaut d’inline_depth est maintenant 16. La valeur par défaut 16 était également en vigueur dans Visual C++ .NET 2003.
- La macro prédéfinie _INTEGRAL_MAX_BITS a été ajoutée. Consultez Macros prédéfinies.
- Les macros prédéfinies _M_CEE _M_CEE_PURE et _M_CEE_SAFE ont été ajoutées. Consultez Macros prédéfinies.
- La macro prédéfinie _M_IX86_FP a été ajoutée.
- La macro prédéfinie _M_X64 a été ajoutée.
- `make_public` pragma
- La syntaxe du pragma `managed`, `unmanaged` a été mise à jour (comporte désormais `push` et `pop`)
- mscorlib.dll est désormais référencé implicitement par la directive `#using`, dans toutes les compilations `/clr`.
- La macro prédéfinie _OPENMP a été ajoutée.
- Le pragma optimize a été mis à jour. a et w ne sont plus des paramètres valides.
- L’attribut no_registry#import a été ajouté.
- Les pragmas `region`, `endregion` ont été ajoutés
- La macro prédéfinie _VC_NODEFAULTLIB a été ajoutée.
- Les macros Variadic sont maintenant implémentées.
- `vtordisp` est déprécié et va être supprimé dans une prochaine version de Visual C++.
- Le pragma `warning` a désormais le spécificateur suppress.

### <a name="new-linker-features"></a>Nouvelles fonctionnalités de l’éditeur de liens

- Les modules (fichiers de sortie MSIL qui ne sont pas de l’assembly) sont désormais autorisés comme entrée de l’éditeur de liens.
- L’option d’éditeur de liens `/ALLOWISOLATION` (Recherche de manifeste) a été ajoutée.
- L’option `/ASSEMBLYRESOURCE` (Incorporer une ressource managée) a été mise à jour pour vous permettre de spécifier désormais le nom de la ressource dans l’assembly, et d’indiquer que la ressource est privée dans l’assembly.
- L’option d’éditeur de liens `/CLRIMAGETYPE` (Spécifier le type d’une image CLR) a été ajoutée.
- L’option d’éditeur de liens `/CLRSUPPORTLASTERROR` (Conserver le dernier code d’erreur pour les appels PInvoke) a été ajoutée.
- L’option d’éditeur de liens `/CLRTHREADATTRIBUTE` (Définir l’attribut de thread CLR) a été ajoutée.
- L’option d’éditeur de liens `/CLRUNMANAGEDCODECHECK` (Ajouter SuppressUnmanagedCodeSecurityAttribute) a été ajoutée.
- L’option d’éditeur de liens `/ERRORREPORT` (Signaler les erreurs internes de L’éditeur de liens) a été ajoutée.
- L’option d’éditeur de liens `/EXETYPE` a été supprimée. L’éditeur de liens ne prend plus en charge la création de pilotes d’appareils Windows 95 et Windows 98. Utilisez un kit DDK approprié pour créer ces pilotes d’appareils. Le mot clé EXETYPE n’est plus valide pour les fichiers de définition de module.
- L’option d’éditeur de liens `/FUNCTIONPADMIN` (Créer une image corrigeable en mémoire) a été ajoutée.
- L’option d’éditeur de liens `/LTCG` est désormais prise en charge sur les modules compilés avec `/clr`. `/LTCG` a également été mis à jour pour prendre en charge les optimisations guidées par profil.
- L’option d’éditeur de liens `/MANIFEST` (Créer un manifeste de l’assembly côte à côte) a été ajoutée.
- L’option d’éditeur de liens `/MANIFESTDEPENDENCY` (Spécifier les dépendances de manifeste) a été ajoutée.
- L’option d’éditeur de liens `/MANIFESTFILE` (Nommer le fichier manifeste) a été ajoutée.
- L’option d’éditeur de liens `/MAPINFO:LINES` a été supprimée.
- L’option d’éditeur de liens `/NXCOMPAT` (Compatible avec la prévention de l’exécution des données) a été ajoutée.
- L’option d’éditeur de liens `/PGD` (Spécifier la base de données pour les optimisations guidées par profil) a été ajoutée.
- L’option d’éditeur de liens `/PROFILE` (Profileur des outils d’analyse des performances) a été ajoutée.
- L’option d’éditeur de liens `/SECTION` (Spécifier les attributs de section) prend désormais en charge la négation d’attributs et ne prend plus en charge les attributs L ou D (liés au VxD).
- Prise en charge Unicode dans le compilateur et l'éditeur de liens
- Désormais, l’option d’éditeur de liens `/VERBOSE` (Imprimer les messages d’avancement) accepte également ICF et REF.
- L’option d’éditeur de liens `/VXD` a été supprimée. L’éditeur de liens ne prend plus en charge la création de pilotes d’appareils Windows 95 et Windows 98. Utilisez un kit DDK approprié pour créer ces pilotes d’appareils. Le mot clé VXD n’est plus valide pour les fichiers de définition de module.
- L’option d’éditeur de liens `/WS` a été supprimée. `/WS` était utilisé pour modifier les images ciblées pour Windows NT 4.0. IMAGECFG.exe -R, suivi du nom de fichier, peut être utilisé à la place de `/WS`. IMAGECFG.exe se trouve sur le CD-ROM Windows NT 4.0, dans SUPPORT\DEBUG\I386\IMAGECFG.EXE.
- L’option d’éditeur de liens `/WX` (Traiter les avertissements de l’Éditeur de liens en tant qu’erreurs) est désormais documentée.

### <a name="new-linker-utility-features"></a>Nouvelles fonctionnalités de l’utilitaire de l’éditeur de liens

- L’option `/ALLOWISOLATION` editbin a été ajoutée.
- L’instruction de fichier de définition de module DESCRIPTION est supprimée. L’éditeur de liens ne prend plus en charge la génération de pilotes d’appareils virtuels.
- L’option `/ERRORREPORT` a été ajoutée à bscmake.exe, dumpbin.exe, editbin.exe et lib.exe.
- L’option `/LTCG` lib a été ajoutée.
- L’option `/NXCOMPAT` editbin a été ajoutée.
- L’option `/RANGE` dumpbin a été ajoutée.
- L’option `/TLS` dumpbin a été ajoutée.
- L’option `/WS` editbin a été supprimée. `/WS` était utilisé pour modifier les images ciblées pour Windows NT 4.0. IMAGECFG.exe -R, suivi du nom de fichier, peut être utilisé à la place de `/WS`. IMAGECFG.exe se trouve sur le CD-ROM Windows NT 4.0, dans SUPPORT\DEBUG\I386\IMAGECFG.EXE.
- L’option /WX[:NO] lib a été ajoutée.

### <a name="new-nmake-features"></a>Nouvelles fonctionnalités NMAKE

- `/ERRORREPORT` a été ajouté.
- `/G` a été ajouté.
- Les règles prédéfinies ont été mises à jour.
- La macro $(MAKE), qui est documentée dans Macros récursives, indique désormais le chemin complet de nmake.exe.

### <a name="new-masm-features"></a>Nouvelles fonctionnalités MASM

- Les expressions MASM sont désormais des valeurs 64 bits. Dans les versions précédentes, les expressions MASM étaient des valeurs 32 bits.
- L’instruction __asm int 3 entraîne désormais la compilation d’une fonction en code natif.
- ALIAS (MASM) est maintenant documentée.
- L’option `/ERRORREPORT` ml.exe et ml64.exe a été ajoutée.
- .FPO est maintenant documentée.
- H2INC.exe n’est pas intégré à Visual C++ 2005. Si vous avez besoin continuer à utiliser H2INC, utilisez H2INC.exe à partir d’une version précédente de Visual C++.
- L’opérateur IMAGEREL a été ajouté.
- L’opérateur HIGH32 a été ajouté.
- L’opérateur LOW32 a été ajouté.
- ml64.exe est une version de MASM pour l’architecture x64. Il assemble les fichiers .asm x64 dans des fichiers objets x64. Le langage assembleur inline n’est pas pris en charge dans le compilateur x64. Les directives MASM suivantes ont été ajoutées pour ml64.exe (x64) :
- .ALLOCSTACK
- .ENDPROLOG
- .PUSHFRAME
- .PUSHREG
- .SAVEREG
- .SAVEXMM128
- . SETFRAME De plus, la directive PROC a été mise à jour avec la syntaxe x64 seulement.
- La directive MMWORD a été ajoutée.
- `/omf` (option de ligne de commande ML.exe) implique désormais `/c`. ML.exe ne prend pas en charge la liaison des objets au format OMF.
- La directive SEGMENT prend désormais en charge des attributs supplémentaires.
- L’opérateur SECTIONREL a été ajouté.
- La directive XMMWORD a été ajoutée.

### <a name="new-crt-features"></a>Nouvelles fonctionnalités CRT

- Des versions sécurisées de plusieurs fonctions ont été ajoutées. Ces fonctions gèrent mieux les erreurs et appliquent des contrôles plus stricts sur les mémoires tampons pour éviter les failles de sécurité courantes. Les nouvelles versions sécurisées sont identifiées par le suffixe **_s**.
- Les versions moins sécurisées existantes de nombreuses fonctions ont été dépréciées. Pour désactiver les avertissements de dépréciation, définissez _CRT_SECURE_NO_WARNINGS.
- De nombreuses fonctions existantes valident désormais leurs paramètres et appellent le gestionnaire de paramètre non valide quand un paramètre non valide est passé.
- De nombreuses fonctions existantes définissent désormais `errno` là où elles ne le faisaient pas auparavant.
- Le typedef `errno_t` avec le type entier a été ajouté. `errno_t` est utilisé chaque fois qu’un paramètre ou type de retour de fonction concerne les codes d’erreur provenant de `errno`. `errno_t` remplace `errcode`.
- Les fonctions dépendantes des paramètres régionaux ont maintenant des versions qui prennent des paramètres régionaux comme paramètre au lieu d’utiliser les paramètres régionaux actuels. Ces nouvelles fonctions ont le suffixe **_l**. Plusieurs nouvelles fonctions ont été ajoutées pour travailler avec des objets de paramètres régionaux. Les nouvelles fonctions incluent `_get_current_locale`, `_create_locale` et `_free_locale`.
- De nouvelles fonctions ont été ajoutées pour prendre en charge le verrouillage et le déverrouillage des descripteurs de fichiers.
- La famille de fonctions `_spawn` ne réinitialise pas errno à zéro en cas de réussite, comme elle le faisait dans les versions antérieures.
- Les versions de la famille de fonctions `printf` qui vous permettent de spécifier l’ordre dans lequel les arguments sont utilisés sont disponibles.
- Unicode est désormais un format de texte pris en charge. La fonction `_open` prend en charge les attributs _O_TEXTW, _O_UTF8 et _O_UTF16. La fonction `fopen` prend en charge la méthode « ccs=ENCODING » de spécification d’un format Unicode.
- Une nouvelle version des bibliothèques CRT générées dans le code managé (MSIL) est désormais disponible et est utilisée durant la compilation avec l’option `/clr` (Compilation pour le Common Language Runtime).
- _fileinfo a été supprimée.
- La taille par défaut de `time_t` est désormais de 64 bits, ce qui étend la plage de `time_t` et de plusieurs des fonctions d’heure jusqu’à l’an 3000.
- La CRT prend désormais en charge la définition des paramètres régionaux par thread. La fonction `_configthreadlocale` a été ajoutée pour prendre en charge cette fonctionnalité.
- Les fonctions `_statusfp2` et `__control87_2` ont été ajoutées pour permettre d’accéder au mot de commande à virgule flottante et de le contrôler sur le processeur à virgule flottante, aussi bien x87 que SSE2.
- Les fonctions `_mkgmtime` et `_mkgmtime64` ont été ajoutées pour prendre en charge la conversion des heures (struct tm) en heures GMT (Greenwich Mean Time).
- Des changements ont été apportés à `swprintf` et `vswprintf` pour une meilleure conformité à la norme.
- Un nouveau fichier d’en-tête, INTRIN. H, fournit des prototypes pour certaines fonctions intrinsèques.
- La fonction `fopen` a désormais un attribut N.
- La fonction `_open` a désormais un attribut _O_NOINHERIT.
- La fonction `atoi` retourne désormais INT_MAX et affecte `errno` à ERANGE en cas de dépassement. Dans les versions précédentes, le comportement de dépassement de capacité n’était pas défini.
- La famille de fonctions `printf` prend en charge la sortie hexadécimale à virgule flottante implémentée conformément à la norme ANSI C99 à l’aide des spécificateurs de type de format %a et %A.
- La famille `printf` prend désormais en charge le préfixe de taille « ll » (long long).
- La fonction `_controlfp` a été optimisée pour obtenir de meilleures performances.
- Des versions Debug de certaines fonctions ont été ajoutées.
- `_chgsignl` et `_cpysignl` ont été ajoutés (versions long double).
- Le type `_locale_t` a été ajouté à la table de types.
- La nouvelle macro `_countof` a été ajoutée pour calculer le nombre d’éléments présents dans un tableau.
- Dans la rubrique relative à chaque fonction, une section sur les équivalents .NET Framework a été ajoutée.
- Plusieurs fonctions de chaîne peuvent désormais tronquer les chaînes au lieu de retourner un échec d’exécution quand les mémoires tampons de sortie sont trop petites. Consultez **_TRUNCATE**.
- `_set_se_translator` nécessite désormais l’utilisation de l’option de compilateur `/EHa`.
- `fpos_t` est désormais **__int64** sous `/Za` (pour du code C) et quand __STDC__ est défini manuellement (pour du code C++). Il s’agissait d’un **struct**.
- _CRT_DISABLE_PERFCRIT_LOCKS peuvent améliorer les performances d’E/S de programmes monothread.
- Les noms POSIX ont été dépréciés en faveur des noms conformes à ISO C++ (par exemple, utilisez `_getch` plutôt que `getch`).
- De nouveaux fichiers .obj d’options de lien sont disponibles en mode pur.
- `_recalloc` combine les fonctionnalités de `realloc` et `calloc`.

## <a name="whats-new-for-c-in-visual-studio-2003"></a>Nouveautés de C++ dans Visual Studio 2003

### <a name="compiler"></a>Compilateur

- Informations sur la façon d’exécuter une application Extensions managées pour C++ générée avec le compilateur de la version actuelle sur une version précédente du runtime.
- Questions fréquentes (FAQ) sur les extensions managées pour C++.
- Une procédure pas à pas a été ajoutée afin de savoir comment porter une application native existante pour utiliser des Extensions managées pour C++ : Procédure pas à pas : portage d’une application C++ native pour interagir avec les composants du .NET Framework.
- Vous pouvez maintenant créer un délégué sur une méthode d’un type valeur.
- La conformité du compilateur à la norme C++ a été considérablement améliorée pour Visual C++ .NET 2003.
- L’option de compilateur `/arch` a été ajoutée.
- `/Gf` est déprécié et va être supprimé dans la prochaine version de Visual C++.
- L’option de compilateur `/G7` a été ajoutée.
- L’option de compilateur `/GS` a été améliorée pour protéger les variables locales contre les dépassements de mémoire tampon directs.
- L’option de compilateur `/noBool` a été supprimée. Le compilateur autorise désormais l’affichage de **bool** en tant que mot clé uniquement (et non en tant qu’identificateur) dans un fichier de code source C++.
- Le type **long long** est désormais disponible en tant que **typedef** de **__int64**. Notez qu’il n’existe pas encore de prise en charge de **long long** dans CRT.
- L’option de compilateur `/Zm` spécifie désormais la limite d’allocation de mémoire de l’en-tête précompilé.
- L’intrinsèque _InterlockedCompareExchange est désormais documenté.
- L’intrinsèque _InterlockedDecrement est désormais documenté.
- L’intrinsèque _InterlockedExchange est désormais documenté.
- L’intrinsèque _InterlockedExchangeAdd est désormais documenté.
- L’intrinsèque _InterlockedIncrement est désormais documenté.
- L’intrinsèque _ReadWriteBarrier a été ajouté.

### <a name="attributes"></a>Attributs

- L’attribut `implements` est maintenant documenté.

### <a name="linker-features"></a>Fonctionnalités de l’éditeur de liens

Les commutateurs suivants de l’éditeur de liens ont été ajoutés :

- /ASSEMBLYDEBUG
- /ASSEMBLYLINKRESOURCE
- DELAYSIGN
- /KEYFILE
- /KEYCONTAINER
- /SAFESEH

### <a name="masm"></a>MASM

La directive .SAFESEH et l’option `/safeseh` ml.exe ont été ajoutées.

## <a name="see-also"></a>Voir aussi

[Guide du portage et de la mise à niveau de Visual C++](visual-cpp-porting-and-upgrading-guide.md)
