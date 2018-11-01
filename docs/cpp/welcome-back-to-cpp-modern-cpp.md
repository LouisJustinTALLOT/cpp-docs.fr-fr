---
title: Bienvenue dans C++ (Modern C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: a7d82a65141e402e779a428ba32d15ddd70016c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454627"
---
# <a name="welcome-back-to-c-modern-c"></a>Bienvenue dans C++ (Modern C++)

C++ est l'un des langages de programmation les plus couramment utilisés au monde. Les programmes C++ bien écrits sont rapides et efficaces. Ce langage est plus flexible que d'autres, car il permet de créer une large gamme d'applications (jeux divertissants et passionnants, logiciels scientifiques de pointe, pilotes de périphériques, programmes incorporés et applications clientes Windows). Depuis plus de 20 ans, C++ est utilisé pour résoudre des problèmes similaires et beaucoup d'autres problèmes. Ce que vous ne savez peut-être pas, c'est qu'un nombre croissant de programmeurs C++ ont abandonné l'ancienne programmation de type C inélégante au profit de la programmation moderne C++.

L'une des spécifications d'origine du C++ était la compatibilité descendante avec le langage C. Depuis, le C++ a évolué selon plusieurs itérations : C avec classes, spécification du langage C++ d'origine, puis nombreuses améliorations ultérieures. Du fait de cet héritage, C++ est souvent appelé langage de programmation multiparadigme. En C++, vous pouvez effectuer de la programmation de style C purement procédurale qui comprend des pointeurs bruts, des tableaux, des chaînes de caractères se terminant par null, des structures de données personnalisées et d'autres fonctionnalités permettant de bénéficier de hautes performances mais pouvant donner lieu à des bogues et compliquer les choses.  Étant donné que la programmation de style C est chargée de périls comme ceux-ci, l'un des objectifs fondamentaux pour C++ était de sécuriser les programmes et de faciliter leur écriture, leur extension et leur mise à jour. Au départ, C++ comprenait des paradigmes de programmation tels que la programmation orientée objet. Au fil des années, des fonctionnalités ont été ajoutées au langage, ainsi que des bibliothèques standard de structures de données et d'algorithmes largement éprouvées. Ce sont ces ajouts qui ont rendu possible l'existence du style C++ moderne.

Le C++ moderne met en avant les aspects suivants :

- Portée basée sur la pile au lieu d'une portée globale statique ou de tas.

- Inférence de type automatique au lieu de noms de types explicites.

- Pointeurs intelligents au lieu de pointeurs bruts.

- `std::string` et `std::wstring` types (consultez [ \<chaîne >](../standard-library/string.md)) au lieu de brutes `char[]` tableaux.

- [Bibliothèque C++ Standard](../standard-library/cpp-standard-library-header-files.md) comme conteneurs `vector`, `list`, et `map` au lieu des tableaux bruts ou des conteneurs personnalisés. Consultez [ \<vecteur >](../standard-library/vector.md), [ \<liste >](../standard-library/list.md), et [ \<carte >](../standard-library/map.md).

- Bibliothèque C++ Standard [algorithmes](../standard-library/algorithm.md) au lieu de manuellement des algorithmes codés.

- Exceptions, pour signaler et gérer les conditions d'erreur.

- Communication entre les threads à l’aide de la bibliothèque Standard C++ sans verrou `std::atomic<>` (consultez [ \<atomique >](../standard-library/atomic.md)) au lieu d’autres mécanismes de communication entre threads.

- Inline [fonctions lambda](../cpp/lambda-expressions-in-cpp.md) au lieu de petites fonctions implémentées séparément.

- Plage de boucles for basées à écrire des boucles plus fiables, utilisables avec des tableaux, des conteneurs de bibliothèque Standard C++ et Windows Runtime collections sous la forme `for ( for-range-declaration : expression )`. Fait partie de la prise en charge du langage principal. Pour plus d’informations, consultez [Range-based pour instruction (C++)](../cpp/range-based-for-statement-cpp.md).

Le langage C++ lui-même a également évolué. Comparez les extraits de code suivants. Cet extrait montre comment les choses se passaient en C++ :

```cpp
#include <vector>

void f()
{
    // Assume circle and shape are user-defined types
    circle* p = new circle( 42 );
    vector<shape*> v = load_shapes();

    for( vector<circle*>::iterator i = v.begin(); i != v.end(); ++i ) {
        if( *i && **i == *p )
            cout << **i << " is a match\n";
    }

    // CAUTION: If v's pointers own the objects, then you
    // must delete them all before v goes out of scope.
    // If v's pointers do not own the objects, and you delete
    // them here, any code that tries to dereference copies
    // of the pointers will cause null pointer exceptions.
    for( vector<circle*>::iterator i = v.begin();
            i != v.end(); ++i ) {
        delete *i; // not exception safe
    }

    // Don't forget to delete this, too.
    delete p;
} // end f()
```

Voici comment la même opération est accomplie en C++ moderne :

```cpp
#include <memory>
#include <vector>

void f()
{
    // ...
    auto p = make_shared<circle>( 42 );
    vector<shared_ptr<shape>> v = load_shapes();

    for( auto& s : v )
    {
        if( s && *s == *p )
        {
            cout << *s << " is a match\n";
        }
    }
}
```

En C++ moderne, il est inutile d'utiliser new/delete ou une gestion des exceptions explicite car vous pouvez utiliser des pointeurs intelligents à la place. Lorsque vous utilisez le **automatique** déduction de type et [fonction lambda](../cpp/lambda-expressions-in-cpp.md), vous pouvez écrire du code plus rapide, renforcer et mieux le comprendre. Et basées sur une plage **pour** boucle est plus clair, plus facile à utiliser et moins sujette aux erreurs inattendues que le style de C **pour** boucle. Vous pouvez utiliser le code réutilisable avec un minimum de lignes de code pour écrire votre application. Et vous pouvez rendre ce code sécurisé du point de vue des exceptions et de la mémoire, et n'avoir aucune allocation/désallocation ou code d'erreur à traiter.

Le C++ moderne incorpore deux genres de polymorphisme : au moment de la compilation, via des modèles, et au moment de l'exécution, via l'héritage et la virtualisation. Vous pouvez combiner ces deux genres de polymorphisme pour obtenir un effet remarquable. Le modèle de bibliothèque Standard C++ `shared_ptr` utilise des méthodes virtuelles internes pour accomplir son effacement de type apparemment sans effort. Mais n'abusez pas de la virtualisation pour le polymorphisme lorsqu'un modèle est plus approprié. Les modèles peuvent être très puissants.

Si vous accédez à C++ depuis un autre langage, en particulier un langage managé dans lequel la plupart des types sont des types référence et très peu sont des types valeur, sachez que les classes C++ sont des types valeur par défaut. Mais vous pouvez les spécifier comme types référence pour activer le comportement polymorphe qui prend en charge la programmation orientée objet. Une perspective utile : les types valeur concernent davantage la mémoire et le contrôle de disposition, alors que les types référence concernent davantage les classes de base et les fonctions virtuelles pour la prise en charge du polymorphisme. Par défaut, les types valeur sont copiables. Ils ont chacun un constructeur de copie et un opérateur d'assignation de copie. Lorsque vous spécifiez un type référence, rendez la classe impossible à copier (désactivez le constructeur de copie et copiez l'opérateur d'affectation) et utilisez un destructeur virtuel, ce qui assure la prise en charge du polymorphisme. Les types valeur concernent également le contenu qui, en cas de copie, vous donne deux valeurs distinctes que vous pouvez modifier séparément. Mais les types référence concernent l'identité (quel que soit le type d'objet) et, pour cette raison, ils sont parfois appelés types polymorphes.

C++ connaît une renaissance car la puissance est à nouveau reine. Les langages comme Java et C# sont suffisants lorsque la productivité du programmeur est importante, mais ils montrent leurs limites lorsque la puissance et les performances sont primordiales. Pour obtenir des performances et une puissance élevées, surtout sur les appareils qui ont du matériel informatique limité, rien ne surpasse le C++ moderne.

Non seulement le langage est moderne, mais les outils de développement le sont également. Visual Studio rend toutes les parties du cycle de développement robustes et efficaces. Il inclut des outils de gestion du cycle de vie des applications (Application Lifecycle Management), des améliorations de l'IDE comme IntelliSense, des mécanismes pratiques pour les outils comme XAML, ainsi que des outils de génération, de débogage et ainsi de suite.

Les articles de cette partie de la documentation fournissent des recommandations de haut niveau et des meilleures pratiques en ce qui concerne les fonctionnalités et les techniques les plus importantes pour l’écriture de programmes C++ modernes.

- [Système de Type C++](../cpp/cpp-type-system-modern-cpp.md)

- [Constructeurs d’initialisation uniforme et de délégation](../cpp/uniform-initialization-and-delegating-constructors.md)

- [Durée de vie et de gestion des ressources](../cpp/object-lifetime-and-resource-management-modern-cpp.md)

- [Ressources propres objets (RAII)](../cpp/objects-own-resources-raii.md)

- [Pointeurs intelligents](../cpp/smart-pointers-modern-cpp.md)

- [Pimpl pour l’Encapsulation au moment de la compilation](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md)

- [Conteneurs](../cpp/containers-modern-cpp.md)

- [Algorithmes](../cpp/algorithms-modern-cpp.md)

- [Chaîne et les e/s de la mise en forme (C++ moderne)](../cpp/string-and-i-o-formatting-modern-cpp.md)

- [Erreurs et exceptions](../cpp/errors-and-exception-handling-modern-cpp.md)

- [Portabilité aux limites ABI](../cpp/portability-at-abi-boundaries-modern-cpp.md)

Pour plus d’informations, consultez l’article StackOverflow [quels idiomes C++ sont déconseillés dans C ++ 11](https://stackoverflow.com/questions/9299101/which-c-idioms-are-deprecated-in-c11).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Expressions lambda](../cpp/lambda-expressions-in-cpp.md)<br/>
[Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)<br/>
[Conformité du langage Visual C++](../visual-cpp-language-conformance.md)