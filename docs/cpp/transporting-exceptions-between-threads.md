---
title: Transport d’exceptions entre les threads | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99f2d785e9f7ab7fa91f51d22299ebab0f39197e
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942066"
---
# <a name="transporting-exceptions-between-threads"></a>Transport des exceptions entre les threads

Visual C++ prend en charge *transport d’une exception* à partir d’un seul thread à un autre. Le transport des exceptions vous permet d'intercepter une exception dans un thread, puis faire en sorte que l'exception semble levée dans un thread différent. Par exemple, utilisez cette fonctionnalité pour écrire une application multithread où le thread principal gère toutes les exceptions levées par les threads secondaires. Le gestion des exceptions est utile principalement aux développeurs qui créent des bibliothèques ou systèmes de programmation parallèle. Pour implémenter le transport des exceptions, Visual C++ fournit la [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) type et le [current_exception](../standard-library/exception-functions.md#current_exception), [rethrow_exception](../standard-library/exception-functions.md#rethrow_exception), et [make_ exception_ptr](../standard-library/exception-functions.md#make_exception_ptr) fonctions.

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

|Paramètre|Description|
|---------------|-----------------|
|*Non spécifié*|Une classe interne non spécifiée utilisée pour implémenter le type `exception_ptr`.|
|*p*|Un objet `exception_ptr` qui référence une exception.|
|*E*|Une classe représentant une exception.|
|*e*|Une instance de la classe de paramètre `E`.|

## <a name="return-value"></a>Valeur de retour

La fonction `current_exception` retourne un objet `exception_ptr` qui référence l'exception actuellement en cours. Si aucune exception n'est en cours, la fonction retourne un objet `exception_ptr` qui n'est associé à aucune exception.

Le `make_exception_ptr` fonction renvoie une `exception_ptr` objet qui fait référence à l’exception spécifiée par le *e* paramètre.

## <a name="remarks"></a>Notes

### <a name="scenario"></a>Scénario

Imaginez que vous souhaitiez créer une application capable d'évoluer afin de gérer une quantité de travail variable. Pour atteindre cet objectif, vous concevez une application multithread où un thread principal initial crée autant de threads secondaires nécessaires pour effectuer le travail. Les threads secondaires aident le thread principal à gérer les ressources, équilibrer les charges et améliorer le débit. Lorsque vous distribuez du travail, l'application multithread fonctionne mieux qu'une application à un seul thread.

Toutefois, si un thread secondaire lève une exception, il faut que le thread principal la gère. C'est parce que votre application doit gérer des exceptions de façon cohérente et unifiée, indépendamment du nombre de threads secondaires.

### <a name="solution"></a>Solution

Pour gérer le scénario précédent, la norme C++ prend en charge le transport d'une exception entre les threads. Si un thread secondaire lève une exception, cette exception devient le *exception actuelle*. Par analogie au monde réel, l’exception actuelle est dite *en vol*. L'exception actuelle est en vol depuis l'instant où elle est levée jusqu'au moment où le gestionnaire d'exceptions qui permet de les intercepter retourne une valeur.

Le thread secondaire peut intercepter l’exception actuelle dans un **catch** bloquer, puis appelez le `current_exception` (fonction) pour stocker l’exception dans un `exception_ptr` objet. L'objet `exception_ptr` doit être disponible pour le thread secondaire et le thread principal. Par exemple, l'objet `exception_ptr` peut être une variable globale dont l'accès est contrôlé par un mutex. Le terme *transporter une exception* signifie une exception dans un seul thread peut être convertie en un formulaire qui est accessible par un autre thread.

Ensuite, le thread principal appelle la fonction `rethrow_exception`, qui extrait puis lève l'exception de l'objet `exception_ptr`. Lorsque l'exception est levée, elle devient l'exception actuelle dans le thread principal. Autrement dit, l'exception semble provenir du thread principal.

Enfin, le thread principal peut intercepter l’exception actuelle dans un **catch** bloquer et puis le traiter ou l’envoyer à un gestionnaire d’exceptions de niveau supérieur. Sinon, le thread principal peut ignorer l'exception et permettre la fin du processus.

La plupart des applications n'ont pas besoin de transporter des exceptions entre les threads. Toutefois, cette fonctionnalité est utile dans un système informatique parallèle, car le système peut diviser le travail parmi les threads secondaires, les processeurs ou les cœurs. Dans un environnement informatique parallèle, un thread unique dédié peut gérer toutes les exceptions dans les threads secondaires et peut présenter un modèle cohérent de gestion des exceptions pour toute application.

Pour plus d’informations sur la proposition de comité de normalisation C++, recherchez sur Internet le numéro de document N2179, intitulé « Language Support for Transporting Exceptions between Threads ».

### <a name="exception-handling-models-and-compiler-options"></a>Options du compilateur et modèles de gestion des exceptions

Le modèle de gestion des exceptions de votre application détermine s'il peut intercepter et déplacer une exception. Visual C++ prend en charge trois modèles capables de gérer les exceptions C++, les exceptions SEH (gestion structurée des exceptions), et les exceptions CLR (Common Langage Runtime). Utilisez le [/EH](../build/reference/eh-exception-handling-model.md) et [/CLR](../build/reference/clr-common-language-runtime-compilation.md) options du compilateur pour spécifier le modèle de gestion des exceptions de votre application.

Seule la combinaison suivante des options du compilateur et des instructions de programmation peut transporter une exception. D'autres combinaisons peuvent ou ne peuvent pas intercepter des exceptions, mais ne peuvent pas transporter des exceptions.

- Le **/EHa** option du compilateur et le **catch** instruction peut transporter des exceptions SEH et C++.

- Le **/EHa**, **/EHs**, et **/EHsc** options du compilateur et le **catch** instruction peut transporter des exceptions C++.

- Le **/CLR** option du compilateur et le **catch** instruction peut transporter des exceptions C++. Le **/CLR** option du compilateur implique la spécification de la **/EHa** option. Notez que le compilateur ne prend pas en charge le transport des exceptions managées. Il s’agit, car les exceptions managées, qui sont dérivées de la [classe System.Exception](../standard-library/exception-class.md), sont déjà des objets que vous pouvez vous déplacer entre les threads à l’aide des fonctionnalités du common language runtime.

   > [!IMPORTANT]
   > Nous vous recommandons de spécifier le **/EHsc** option de compilateur et catch uniquement des exceptions C++. Vous vous exposez à une menace de sécurité si vous utilisez le **/EHa** ou **/CLR** option du compilateur et un **catch** instruction des points de suspension  *déclaration d’exception* (`catch(...)`). Vous envisagez probablement d’utiliser le **catch** instruction pour capturer quelques exceptions spécifiques. Toutefois, l'instruction `catch(...)` capture toutes les exceptions C++ et SEH, notamment les exceptions inattendues qui devraient s'avérer irrécupérables. Si vous ignorez ou traitez mal une exception inattendue, le code malveillant peut utiliser cette possibilité pour fragiliser la sécurité de votre programme.

## <a name="usage"></a>Utilisation

Les sections suivantes décrivent comment transporter des exceptions à l’aide de la `exception_ptr` type et le `current_exception`, `rethrow_exception`, et `make_exception_ptr` fonctions.

## <a name="exceptionptr-type"></a>Type d'exception_ptr

Utilisez un objet `exception_ptr` pour référencer l'exception actuelle ou une instance d'une exception spécifiée par l'utilisateur. Dans l’implémentation Microsoft, une exception est représentée par une structure [EXCEPTION_RECORD](https://msdn.microsoft.com/library/windows/desktop/aa363082). Chaque objet `exception_ptr` inclut un champ de référence d'exception qui pointe vers une copie de la structure `EXCEPTION_RECORD` qui représente l'exception.

Lorsque vous déclarez une variable `exception_ptr`, la variable n'est associée à aucune exception. Autrement dit, son champ de référence d'exception est NULL. Ce type d’objet `exception_ptr` est appelé *exception_ptr null*.

Utilisez la fonction `current_exception` ou `make_exception_ptr` pour assigner une exception à un objet `exception_ptr`. Lorsque vous assignez une exception à une variable `exception_ptr`, le champ de référence de l'exception de la variable pointe vers une copie de l'exception. Si la mémoire est insuffisante pour copier l’exception, le champ de référence d’exception pointe vers une copie d’une exception [std::bad_alloc](../standard-library/bad-alloc-class.md). Si le `current_exception` ou `make_exception_ptr` fonction ne peut pas copier l’exception pour toute autre raison, la fonction appelle le [Terminer](../c-runtime-library/reference/terminate-crt.md) (fonction) pour quitter le processus en cours.

En dépit de son nom, un objet `exception_ptr` n'est pas lui-même un pointeur. Il ne respecte pas la sémantique des pointeurs et ne peut pas être utilisé avec l’accès au membre de pointeur (`->`) ou d’indirection (`*`) opérateurs. L'objet `exception_ptr` n'a aucune donnée membre ou fonction membre publique.

### <a name="comparisons"></a>Comparaisons

Vous pouvez utiliser les opérateurs égal (`==`) et non égal (`!=`) pour comparer deux objets `exception_ptr`. Les opérateurs ne comparent pas la valeur binaire (modèle binaire) des structures `EXCEPTION_RECORD` qui représentent les exceptions. À la place, les opérateurs comparent les adresses dans le domaine de référence d'exception des objets `exception_ptr`. Par conséquent, une exception `exception_ptr` null et la valeur NULL sont considérées comme égales.

## <a name="currentexception-function"></a>Fonction current_exception

Appelez le `current_exception` fonctionner dans un **catch** bloc. Si une exception est en vol et la **catch** bloc peut intercepter l’exception, le `current_exception` fonction renvoie une `exception_ptr` objet qui fait référence à l’exception. Sinon, la fonction retourne un objet `exception_ptr` null.

### <a name="details"></a>Détails

Le `current_exception` fonction capture l’exception qui est en vol même si le **catch** instruction spécifie un [déclaration d’exception](../cpp/try-throw-and-catch-statements-cpp.md) instruction.

Le destructeur de l’exception actuelle est appelé à la fin de la **catch** bloquer si vous ne pas lever à nouveau l’exception. Toutefois, même si vous appelez la fonction `current_exception` dans le destructeur, celle-ci retourne un objet `exception_ptr` qui référence l’exception actuelle.

Les appels successifs à la fonction `current_exception` retournent des objets `exception_ptr` qui font référence à des copies de l'exception actuelle. Par conséquent, les objets sont considérés comme inégaux car ils font référence à des copies, bien que les copies aient la même valeur binaire.

### <a name="seh-exceptions"></a>Exceptions SEH

Si vous utilisez le **/EHa** option du compilateur, vous pouvez intercepter une exception SEH dans C++ **catch** bloc. La fonction `current_exception` retourne un objet `exception_ptr` qui référence l'exception SEH. Et le `rethrow_exception` fonction lève une exception SEH si vous l’appelez avec thetransported `exception_ptr` objet comme argument.

Le `current_exception` fonction retourne une valeur null `exception_ptr` si vous l’appelez dans une gestion des exceptions structurées **__finally** Gestionnaire de terminaisons, un **__except** Gestionnaire d’exceptions, ou le **__except**expression de filtre.

Une exception transportée ne prend pas en charge les exceptions imbriquées. Une exception imbriquée se produit lorsqu'une autre exception est levée pendant la gestion d'une exception. Si vous interceptez une exception imbriquée, les données membres `EXCEPTION_RECORD.ExceptionRecord` pointent vers une chaîne de structures `EXCEPTION_RECORD` qui décrivent les exceptions associées. La fonction `current_exception` ne prend pas en charge les exceptions imbriquées car elle retourne un objet `exception_ptr` dont la donnée membre `ExceptionRecord` est mise à zéro.

Si vous interceptez une exception SEH, vous devez gérer la mémoire référencée par tout pointeur dans le tableau de données membres `EXCEPTION_RECORD.ExceptionInformation`. Vous devez vous assurer que la mémoire est valide pendant la durée de vie de l'objet `exception_ptr` correspondant, et que cette mémoire est libérée lorsque l'objet `exception_ptr` est supprimé.

Vous pouvez utiliser les fonctions de traduction d'exceptions structurées avec la fonctionnalité de transport d'exceptions. Si une exception SEH est traduite en une exception C++, la fonction `current_exception` retourne `exception_ptr` qui référence l'exception traduite au lieu de l'exception SEH originale. La fonction `rethrow_exception` lève ultérieurement l'exception traduite, pas l'exception d'origine. Pour plus d’informations sur les fonctions de traduction d’exceptions, consultez [_set_se_translator](../c-runtime-library/reference/set-se-translator.md).

## <a name="rethrowexception-function"></a>Fonction rethrow_exception

Après avoir enregistré une exception interceptée dans un objet `exception_ptr`, le thread principal peut traiter l'objet. Dans votre thread principal, appelez la fonction `rethrow_exception` avec l'objet `exception_ptr` en tant qu'argument. La fonction `rethrow_exception` extrait l'exception de l'objet `exception_ptr` puis lève l'exception dans le contexte du thread principal. Si le *p* paramètre de la `rethrow_exception` fonction est une valeur null `exception_ptr`, la fonction lève [std::bad_exception](../standard-library/bad-exception-class.md).

L'exception extraite est maintenant l'exception actuelle dans le thread principal, et vous pouvez la gérer comme n'importe quelle autre exception. Si vous interceptez l’exception, vous pouvez gérer immédiatement ou utiliser un **lever** instruction pour l’envoyer à un gestionnaire d’exceptions de niveau supérieur. Sinon, ne faites rien et laissez le gestionnaire d'exceptions systèmes par défaut terminer le processus.

## <a name="makeexceptionptr-function"></a>Fonction make_exception_ptr

La fonction `make_exception_ptr` prend une instance de classe comme argument puis retourne un `exception_ptr` qui référence l'instance. Généralement, vous spécifiez un objet de [classe exception](../standard-library/exception-class.md) comme argument pour la fonction `make_exception_ptr`, bien que tout objet de classe puisse être l’argument.

Appelant le `make_exception_ptr` fonction équivaut à lever une exception C++, intercepter dans un **catch** bloc, puis en appelant le `current_exception` fonction pour retourner une `exception_ptr` objet qui fait référence à l’exception. L'implémentation Microsoft de la fonction `make_exception_ptr` est plus efficace que le fait de lever puis d'intercepter une exception.

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

## <a name="requirements"></a>Configuration requise

**En-tête :** \<exception>

## <a name="see-also"></a>Voir aussi

- [Gestion des exceptions](../cpp/exception-handling-in-visual-cpp.md)
- [/EH (Modèle de gestion des exceptions)](../build/reference/eh-exception-handling-model.md)
- [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md)
