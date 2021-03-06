---
description: 'En savoir plus sur : le transport d’exceptions entre les threads'
title: Transport des exceptions entre les threads
ms.date: 05/07/2019
helpviewer_keywords:
- std::current_exception
- transporting exceptions between threads
- std::copy_exception
- exception_ptr
- std::exception_ptr
- std::rethrow_exception
- current_exception
- transport exceptions between threads
- copy_exception
- rethrow_exception
- move exceptions between threads
ms.assetid: 5c95d57b-acf5-491f-8122-57c5df0edd98
ms.openlocfilehash: 8b62937c95c755304ab5766185168fad618a53aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313669"
---
# <a name="transporting-exceptions-between-threads"></a>Transport des exceptions entre les threads

Le compilateur Microsoft C++ (MSVC) prend en charge le *transport d’une exception* d’un thread à un autre. Le transport des exceptions vous permet d'intercepter une exception dans un thread, puis faire en sorte que l'exception semble levée dans un thread différent. Par exemple, utilisez cette fonction pour écrire une application multithread où le thread principal gère toutes les exceptions levées par les threads secondaires. Le gestion des exceptions est utile principalement aux développeurs qui créent des bibliothèques ou systèmes de programmation parallèle. Pour implémenter les exceptions de transport, MSVC fournit le type de [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) et les fonctions [current_exception](../standard-library/exception-functions.md#current_exception), [rethrow_exception](../standard-library/exception-functions.md#rethrow_exception)et [make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr) .

## <a name="syntax"></a>Syntaxe

```cpp
namespace std
{
   typedef unspecified exception_ptr;
   exception_ptr current_exception();
   void rethrow_exception(exception_ptr p);
   template<class E>
       exception_ptr make_exception_ptr(E e) noexcept;
}
```

### <a name="parameters"></a>Paramètres

*non spécifié*\
Une classe interne non spécifiée utilisée pour implémenter le type `exception_ptr`.

*p*\
Un objet `exception_ptr` qui référence une exception.

*Envoyer*\
Une classe représentant une exception.

*Envoyer*\
Une instance de la classe de paramètre `E`.

## <a name="return-value"></a>Valeur retournée

La fonction `current_exception` retourne un objet `exception_ptr` qui référence l'exception actuellement en cours. Si aucune exception n'est en cours, la fonction retourne un objet `exception_ptr` qui n'est associé à aucune exception.

La `make_exception_ptr` fonction retourne un `exception_ptr` objet qui fait référence à l’exception spécifiée par le paramètre *e* .

## <a name="remarks"></a>Notes

### <a name="scenario"></a>Scénario

Imaginez que vous souhaitiez créer une application capable d'évoluer afin de gérer une quantité de travail variable. Pour atteindre cet objectif, vous concevez une application multithread où un thread principal initial crée autant de threads secondaires nécessaires pour effectuer le travail. Les threads secondaires aident le thread principal à gérer les ressources, équilibrer les charges et améliorer le débit. Lorsque vous distribuez du travail, l'application multithread fonctionne mieux qu'une application à un seul thread.

Toutefois, si un thread secondaire lève une exception, il faut que le thread principal la gère. C'est parce que votre application doit gérer des exceptions de façon cohérente et unifiée, indépendamment du nombre de threads secondaires.

### <a name="solution"></a>Solution

Pour gérer le scénario précédent, la norme C++ prend en charge le transport d'une exception entre les threads. Si un thread secondaire lève une exception, cette exception devient l' *exception actuelle*. Par analogie au monde réel, l’exception actuelle est dite *en vol*. L'exception actuelle est en vol depuis l'instant où elle est levée jusqu'au moment où le gestionnaire d'exceptions qui permet de les intercepter retourne une valeur.

Le thread secondaire peut intercepter l’exception actuelle dans un **`catch`** bloc, puis appeler la `current_exception` fonction pour stocker l’exception dans un `exception_ptr` objet. L'objet `exception_ptr` doit être disponible pour le thread secondaire et le thread principal. Par exemple, l'objet `exception_ptr` peut être une variable globale dont l'accès est contrôlé par un mutex. Le terme *transport d’une exception* signifie qu’une exception dans un thread peut être convertie en un formulaire accessible par un autre thread.

Ensuite, le thread principal appelle la fonction `rethrow_exception`, qui extrait puis lève l'exception de l'objet `exception_ptr`. Lorsque l'exception est levée, elle devient l'exception actuelle dans le thread principal. Autrement dit, l'exception semble provenir du thread principal.

Enfin, le thread principal peut intercepter l’exception actuelle dans un **`catch`** bloc, puis la traiter ou la lever à un gestionnaire d’exceptions de niveau supérieur. Sinon, le thread principal peut ignorer l'exception et permettre la fin du processus.

La plupart des applications n'ont pas besoin de transporter des exceptions entre les threads. Toutefois, cette fonctionnalité est utile dans un système informatique parallèle, car le système peut diviser le travail parmi les threads secondaires, les processeurs ou les cœurs. Dans un environnement informatique parallèle, un thread unique dédié peut gérer toutes les exceptions dans les threads secondaires et peut présenter un modèle cohérent de gestion des exceptions pour toute application.

Pour plus d’informations sur la proposition de comité de normalisation C++, recherchez sur Internet le numéro de document N2179, intitulé « Language Support for Transporting Exceptions between Threads ».

### <a name="exception-handling-models-and-compiler-options"></a>Modèles de gestion des exceptions et options du compilateur

Le modèle de gestion des exceptions de votre application détermine s'il peut intercepter et déplacer une exception. Visual C++ prend en charge trois modèles capables de gérer les exceptions C++, les exceptions SEH (gestion structurée des exceptions), et les exceptions CLR (Common Langage Runtime). Utilisez les options du compilateur [/Eh](../build/reference/eh-exception-handling-model.md) et [/CLR](../build/reference/clr-common-language-runtime-compilation.md) pour spécifier le modèle de gestion des exceptions de votre application.

Seule la combinaison suivante des options du compilateur et des instructions de programmation peut transporter une exception. D'autres combinaisons peuvent ou ne peuvent pas intercepter des exceptions, mais ne peuvent pas transporter des exceptions.

- L’option de compilateur **/EHa** et l' **`catch`** instruction peuvent transporter des exceptions SEH et C++.

- Les options de compilateur **/EHa**, **/EHS** et **/EHsc** et l' **`catch`** instruction peuvent transporter des exceptions C++.

- L’option du compilateur **/CLR** et l' **`catch`** instruction peuvent transporter des exceptions C++. L’option du compilateur **/CLR** implique la spécification de l’option **/EHa** . Notez que le compilateur ne prend pas en charge le transport des exceptions managées. Cela est dû au fait que les exceptions managées, dérivées de la [classe System. exception](../standard-library/exception-class.md), sont déjà des objets que vous pouvez déplacer entre les threads à l’aide des fonctionnalités du Common Language Runtime.

   > [!IMPORTANT]
   > Nous vous recommandons de spécifier l’option de compilateur **/EHsc** et d’intercepter uniquement les exceptions C++. Vous vous exposez à une menace de sécurité si vous utilisez l’option de compilateur **/EHa** ou **/CLR** et une **`catch`** instruction avec des points de suspension *exception-declaration* ( `catch(...)` ). Vous envisagez probablement d’utiliser l' **`catch`** instruction pour capturer quelques exceptions spécifiques. Toutefois, l'instruction `catch(...)` capture toutes les exceptions C++ et SEH, notamment les exceptions inattendues qui devraient s'avérer irrécupérables. Si vous ignorez ou traitez mal une exception inattendue, le code malveillant peut utiliser cette possibilité pour fragiliser la sécurité de votre programme.

## <a name="usage"></a>Utilisation

Les sections suivantes décrivent comment transporter des exceptions à l’aide du `exception_ptr` type, et les `current_exception` `rethrow_exception` fonctions, et `make_exception_ptr` .

## <a name="exception_ptr-type"></a>type de exception_ptr

Utilisez un objet `exception_ptr` pour référencer l'exception actuelle ou une instance d'une exception spécifiée par l'utilisateur. Dans l’implémentation Microsoft, une exception est représentée par une structure [EXCEPTION_RECORD](/windows/win32/api/winnt/ns-winnt-exception_record). Chaque objet `exception_ptr` inclut un champ de référence d'exception qui pointe vers une copie de la structure `EXCEPTION_RECORD` qui représente l'exception.

Lorsque vous déclarez une variable `exception_ptr`, la variable n'est associée à aucune exception. Autrement dit, son champ de référence d'exception est NULL. Ce type d’objet `exception_ptr` est appelé *exception_ptr null*.

Utilisez la fonction `current_exception` ou `make_exception_ptr` pour assigner une exception à un objet `exception_ptr`. Lorsque vous assignez une exception à une variable `exception_ptr`, le champ de référence de l'exception de la variable pointe vers une copie de l'exception. Si la mémoire est insuffisante pour copier l’exception, le champ de référence d’exception pointe vers une copie d’une exception [std::bad_alloc](../standard-library/bad-alloc-class.md). Si la `current_exception` `make_exception_ptr` fonction ou ne peut pas copier l’exception pour une autre raison, la fonction appelle la fonction [Terminate](../c-runtime-library/reference/terminate-crt.md) pour quitter le processus en cours.

En dépit de son nom, un objet `exception_ptr` n'est pas lui-même un pointeur. Elle ne respecte pas la sémantique des pointeurs et ne peut pas être utilisée avec les opérateurs d’accès au membre de pointeur ( `->` ) ou d’indirection ( `*` ). L'objet `exception_ptr` n'a aucune donnée membre ou fonction membre publique.

### <a name="comparisons"></a>Comparaisons

Vous pouvez utiliser les opérateurs égal (`==`) et non égal (`!=`) pour comparer deux objets `exception_ptr`. Les opérateurs ne comparent pas la valeur binaire (modèle binaire) des structures `EXCEPTION_RECORD` qui représentent les exceptions. À la place, les opérateurs comparent les adresses dans le domaine de référence d'exception des objets `exception_ptr`. Par conséquent, une exception `exception_ptr` null et la valeur NULL sont considérées comme égales.

## <a name="current_exception-function"></a>current_exception fonction)

Appelez la `current_exception` fonction dans un **`catch`** bloc. Si une exception est en cours et que le **`catch`** bloc peut intercepter l’exception, la `current_exception` fonction retourne un `exception_ptr` objet qui référence l’exception. Sinon, la fonction retourne un objet `exception_ptr` null.

### <a name="details"></a>Détails

La `current_exception` fonction capture l’exception qui est en vol, que l' **`catch`** instruction spécifie ou non une instruction de [déclaration d’exception](../cpp/try-throw-and-catch-statements-cpp.md) .

Le destructeur de l’exception actuelle est appelé à la fin du **`catch`** bloc si vous ne levez pas à nouveau l’exception. Toutefois, même si vous appelez la fonction `current_exception` dans le destructeur, celle-ci retourne un objet `exception_ptr` qui référence l’exception actuelle.

Les appels successifs à la fonction `current_exception` retournent des objets `exception_ptr` qui font référence à des copies de l'exception actuelle. Par conséquent, les objets sont considérés comme inégaux car ils font référence à des copies, bien que les copies aient la même valeur binaire.

### <a name="seh-exceptions"></a>Exceptions SEH

Si vous utilisez l’option de compilateur **/EHa** , vous pouvez intercepter une exception SEH dans un **`catch`** bloc C++. La fonction `current_exception` retourne un objet `exception_ptr` qui référence l'exception SEH. Et la `rethrow_exception` fonction lève l’exception SEH si vous l’appelez avec l' `exception_ptr` objet thetransported comme argument.

La `current_exception` fonction retourne une valeur null `exception_ptr` si vous l’appelez dans un **`__finally`** Gestionnaire de terminaisons SEH, un **`__except`** Gestionnaire d’exceptions ou l' **`__except`** expression de filtre.

Une exception transportée ne prend pas en charge les exceptions imbriquées. Une exception imbriquée se produit lorsqu'une autre exception est levée pendant la gestion d'une exception. Si vous interceptez une exception imbriquée, les données membres `EXCEPTION_RECORD.ExceptionRecord` pointent vers une chaîne de structures `EXCEPTION_RECORD` qui décrivent les exceptions associées. La fonction `current_exception` ne prend pas en charge les exceptions imbriquées car elle retourne un objet `exception_ptr` dont la donnée membre `ExceptionRecord` est mise à zéro.

Si vous interceptez une exception SEH, vous devez gérer la mémoire référencée par tout pointeur dans le tableau de données membres `EXCEPTION_RECORD.ExceptionInformation`. Vous devez vous assurer que la mémoire est valide pendant la durée de vie de l'objet `exception_ptr` correspondant, et que cette mémoire est libérée lorsque l'objet `exception_ptr` est supprimé.

Vous pouvez utiliser les fonctions de traduction d’exceptions structurées avec la fonctionnalité de transport d’exceptions. Si une exception SEH est traduite en une exception C++, la fonction `current_exception` retourne `exception_ptr` qui référence l'exception traduite au lieu de l'exception SEH originale. La fonction `rethrow_exception` lève ultérieurement l'exception traduite, pas l'exception d'origine. Pour plus d’informations sur les fonctions de traduction SE, consultez [_set_se_translator](../c-runtime-library/reference/set-se-translator.md).

## <a name="rethrow_exception-function"></a>rethrow_exception fonction)

Après avoir enregistré une exception interceptée dans un objet `exception_ptr`, le thread principal peut traiter l'objet. Dans votre thread principal, appelez la fonction `rethrow_exception` avec l'objet `exception_ptr` en tant qu'argument. La fonction `rethrow_exception` extrait l'exception de l'objet `exception_ptr` puis lève l'exception dans le contexte du thread principal. Si le paramètre *p* de la `rethrow_exception` fonction est une valeur null `exception_ptr` , la fonction lève [std :: bad_exception](../standard-library/bad-exception-class.md).

L'exception extraite est maintenant l'exception actuelle dans le thread principal, et vous pouvez la gérer comme n'importe quelle autre exception. Si vous interceptez l’exception, vous pouvez la gérer immédiatement ou utiliser une **`throw`** instruction pour l’envoyer à un gestionnaire d’exceptions de niveau supérieur. Sinon, ne faites rien et laissez le gestionnaire d'exceptions systèmes par défaut terminer le processus.

## <a name="make_exception_ptr-function"></a>make_exception_ptr, fonction

La fonction `make_exception_ptr` prend une instance de classe comme argument puis retourne un `exception_ptr` qui référence l'instance. Généralement, vous spécifiez un objet de [classe exception](../standard-library/exception-class.md) comme argument pour la fonction `make_exception_ptr`, bien que tout objet de classe puisse être l’argument.

L’appel de la `make_exception_ptr` fonction équivaut à lever une exception C++, à l’intercepter dans un **`catch`** bloc, puis à appeler la `current_exception` fonction pour retourner un `exception_ptr` objet qui référence l’exception. L'implémentation Microsoft de la fonction `make_exception_ptr` est plus efficace que le fait de lever puis d'intercepter une exception.

En général, une application ne requiert pas la fonction `make_exception_ptr`, et son utilisation est d'ailleurs déconseillée.

## <a name="example"></a>Exemple

L'exemple suivant transporte une exception C++ standard et une exception C++ personnalisée d'un thread à un autre.

```cpp
// transport_exception.cpp
// compile with: /EHsc /MD
#include <windows.h>
#include <stdio.h>
#include <exception>
#include <stdexcept>

using namespace std;

// Define thread-specific information.
#define THREADCOUNT 2
exception_ptr aException[THREADCOUNT];
int           aArg[THREADCOUNT];

DWORD WINAPI ThrowExceptions( LPVOID );

// Specify a user-defined, custom exception.
// As a best practice, derive your exception
// directly or indirectly from std::exception.
class myException : public std::exception {
};
int main()
{
    HANDLE aThread[THREADCOUNT];
    DWORD ThreadID;

    // Create secondary threads.
    for( int i=0; i < THREADCOUNT; i++ )
    {
        aArg[i] = i;
        aThread[i] = CreateThread(
            NULL,       // Default security attributes.
            0,          // Default stack size.
            (LPTHREAD_START_ROUTINE) ThrowExceptions,
            (LPVOID) &aArg[i], // Thread function argument.
            0,          // Default creation flags.
            &ThreadID); // Receives thread identifier.
        if( aThread[i] == NULL )
        {
            printf("CreateThread error: %d\n", GetLastError());
            return -1;
        }
    }

    // Wait for all threads to terminate.
    WaitForMultipleObjects(THREADCOUNT, aThread, TRUE, INFINITE);
    // Close thread handles.
    for( int i=0; i < THREADCOUNT; i++ ) {
        CloseHandle(aThread[i]);
    }

    // Rethrow and catch the transported exceptions.
    for ( int i = 0; i < THREADCOUNT; i++ ) {
        try {
            if (aException[i] == NULL) {
                printf("exception_ptr %d: No exception was transported.\n", i);
            }
            else {
                rethrow_exception( aException[i] );
            }
        }
        catch( const invalid_argument & ) {
            printf("exception_ptr %d: Caught an invalid_argument exception.\n", i);
        }
        catch( const myException & ) {
            printf("exception_ptr %d: Caught a  myException exception.\n", i);
        }
    }
}
// Each thread throws an exception depending on its thread
// function argument, and then ends.
DWORD WINAPI ThrowExceptions( LPVOID lpParam )
{
    int x = *((int*)lpParam);
    if (x == 0) {
        try {
            // Standard C++ exception.
            // This example explicitly throws invalid_argument exception.
            // In practice, your application performs an operation that
            // implicitly throws an exception.
            throw invalid_argument("A C++ exception.");
        }
        catch ( const invalid_argument & ) {
            aException[x] = current_exception();
        }
    }
    else {
        // User-defined exception.
        aException[x] = make_exception_ptr( myException() );
    }
    return TRUE;
}
```

```Output
exception_ptr 0: Caught an invalid_argument exception.
exception_ptr 1: Caught a  myException exception.
```

## <a name="requirements"></a>Spécifications

**En-tête :**\<exception>

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../cpp/exception-handling-in-visual-cpp.md)<br/>
[/EH (modèle de gestion des exceptions)](../build/reference/eh-exception-handling-model.md)<br/>
[/CLR (compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md)
