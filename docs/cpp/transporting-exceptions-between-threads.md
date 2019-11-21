---
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
ms.openlocfilehash: 25b09c508b932a4d1470f6b23f03aa52e62c68cc
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246309"
---
# <a name="transporting-exceptions-between-threads"></a>Transport des exceptions entre les threads

The Microsoft C++ compiler (MSVC) supports *transporting an exception* from one thread to another. Le transport des exceptions vous permet d'intercepter une exception dans un thread, puis faire en sorte que l'exception semble levée dans un thread différent. Par exemple, utilisez cette fonction pour écrire une application multithread où le thread principal gère toutes les exceptions levées par les threads secondaires. Le gestion des exceptions est utile principalement aux développeurs qui créent des bibliothèques ou systèmes de programmation parallèle. To implement transporting exceptions, MSVC provides the [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) type and the [current_exception](../standard-library/exception-functions.md#current_exception), [rethrow_exception](../standard-library/exception-functions.md#rethrow_exception), and [make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr) functions.

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
|*unspecified*|Une classe interne non spécifiée utilisée pour implémenter le type `exception_ptr`.|
|*p*|Un objet `exception_ptr` qui référence une exception.|
|*E*|Une classe représentant une exception.|
|*e*|Une instance de la classe de paramètre `E`.|

## <a name="return-value"></a>Valeur de retour

La fonction `current_exception` retourne un objet `exception_ptr` qui référence l'exception actuellement en cours. Si aucune exception n'est en cours, la fonction retourne un objet `exception_ptr` qui n'est associé à aucune exception.

The `make_exception_ptr` function returns an `exception_ptr` object that references the exception specified by the *e* parameter.

## <a name="remarks"></a>Notes

### <a name="scenario"></a>Scénario

Imaginez que vous souhaitiez créer une application capable d'évoluer afin de gérer une quantité de travail variable. Pour atteindre cet objectif, vous concevez une application multithread où un thread principal initial crée autant de threads secondaires nécessaires pour effectuer le travail. Les threads secondaires aident le thread principal à gérer les ressources, équilibrer les charges et améliorer le débit. Lorsque vous distribuez du travail, l'application multithread fonctionne mieux qu'une application à un seul thread.

Toutefois, si un thread secondaire lève une exception, il faut que le thread principal la gère. C'est parce que votre application doit gérer des exceptions de façon cohérente et unifiée, indépendamment du nombre de threads secondaires.

### <a name="solution"></a>Solution

Pour gérer le scénario précédent, la norme C++ prend en charge le transport d'une exception entre les threads. If a secondary thread throws an exception, that exception becomes the *current exception*. By analogy to the real world, the current exception is said to be *in flight*. L'exception actuelle est en vol depuis l'instant où elle est levée jusqu'au moment où le gestionnaire d'exceptions qui permet de les intercepter retourne une valeur.

The secondary thread can catch the current exception in a **catch** block, and then call the `current_exception` function to store the exception in an `exception_ptr` object. L'objet `exception_ptr` doit être disponible pour le thread secondaire et le thread principal. Par exemple, l'objet `exception_ptr` peut être une variable globale dont l'accès est contrôlé par un mutex. The term *transport an exception* means an exception in one thread can be converted to a form that can be accessed by another thread.

Ensuite, le thread principal appelle la fonction `rethrow_exception`, qui extrait puis lève l'exception de l'objet `exception_ptr`. Lorsque l'exception est levée, elle devient l'exception actuelle dans le thread principal. Autrement dit, l'exception semble provenir du thread principal.

Finally, the primary thread can catch the current exception in a **catch** block and then process it or throw it to a higher level exception handler. Sinon, le thread principal peut ignorer l'exception et permettre la fin du processus.

La plupart des applications n'ont pas besoin de transporter des exceptions entre les threads. Toutefois, cette fonctionnalité est utile dans un système informatique parallèle, car le système peut diviser le travail parmi les threads secondaires, les processeurs ou les cœurs. Dans un environnement informatique parallèle, un thread unique dédié peut gérer toutes les exceptions dans les threads secondaires et peut présenter un modèle cohérent de gestion des exceptions pour toute application.

Pour plus d’informations sur la proposition de comité de normalisation C++, recherchez sur Internet le numéro de document N2179, intitulé « Language Support for Transporting Exceptions between Threads ».

### <a name="exception-handling-models-and-compiler-options"></a>Exception-handling models and compiler options

Le modèle de gestion des exceptions de votre application détermine s'il peut intercepter et déplacer une exception. Visual C++ prend en charge trois modèles capables de gérer les exceptions C++, les exceptions SEH (gestion structurée des exceptions), et les exceptions CLR (Common Langage Runtime). Use the [/EH](../build/reference/eh-exception-handling-model.md) and [/clr](../build/reference/clr-common-language-runtime-compilation.md) compiler options to specify your application's exception-handling model.

Seule la combinaison suivante des options du compilateur et des instructions de programmation peut transporter une exception. D'autres combinaisons peuvent ou ne peuvent pas intercepter des exceptions, mais ne peuvent pas transporter des exceptions.

- The **/EHa** compiler option and the **catch** statement can transport SEH and C++ exceptions.

- The **/EHa**, **/EHs**, and **/EHsc** compiler options and the **catch** statement can transport C++ exceptions.

- The **/CLR** compiler option and the **catch** statement can transport C++ exceptions. The **/CLR** compiler option implies specification of the **/EHa** option. Notez que le compilateur ne prend pas en charge le transport des exceptions managées. This is because managed exceptions, which are derived from the [System.Exception class](../standard-library/exception-class.md), are already objects that you can move between threads by using the facilities of the common languange runtime.

   > [!IMPORTANT]
   > We recommend that you specify the **/EHsc** compiler option and catch only C++ exceptions. You expose yourself to a security threat if you use the **/EHa** or **/CLR** compiler option and a **catch** statement with an ellipsis *exception-declaration* (`catch(...)`). You probably intend to use the **catch** statement to capture a few specific exceptions. Toutefois, l'instruction `catch(...)` capture toutes les exceptions C++ et SEH, notamment les exceptions inattendues qui devraient s'avérer irrécupérables. Si vous ignorez ou traitez mal une exception inattendue, le code malveillant peut utiliser cette possibilité pour fragiliser la sécurité de votre programme.

## <a name="usage"></a>Utilisation

The following sections describe how to transport exceptions by using the `exception_ptr` type, and the `current_exception`, `rethrow_exception`, and `make_exception_ptr` functions.

## <a name="exception_ptr-type"></a>exception_ptr type

Utilisez un objet `exception_ptr` pour référencer l'exception actuelle ou une instance d'une exception spécifiée par l'utilisateur. Dans l’implémentation Microsoft, une exception est représentée par une structure [EXCEPTION_RECORD](/windows/win32/api/winnt/ns-winnt-exception_record). Chaque objet `exception_ptr` inclut un champ de référence d'exception qui pointe vers une copie de la structure `EXCEPTION_RECORD` qui représente l'exception.

Lorsque vous déclarez une variable `exception_ptr`, la variable n'est associée à aucune exception. Autrement dit, son champ de référence d'exception est NULL. Ce type d’objet `exception_ptr` est appelé *exception_ptr null*.

Utilisez la fonction `current_exception` ou `make_exception_ptr` pour assigner une exception à un objet `exception_ptr`. Lorsque vous assignez une exception à une variable `exception_ptr`, le champ de référence de l'exception de la variable pointe vers une copie de l'exception. Si la mémoire est insuffisante pour copier l’exception, le champ de référence d’exception pointe vers une copie d’une exception [std::bad_alloc](../standard-library/bad-alloc-class.md). If the `current_exception` or `make_exception_ptr` function cannot copy the exception for any other reason, the function calls the [terminate](../c-runtime-library/reference/terminate-crt.md) function to exit the current process.

En dépit de son nom, un objet `exception_ptr` n'est pas lui-même un pointeur. It does not obey pointer semantics and cannot be used with the pointer member access (`->`) or indirection (`*`) operators. L'objet `exception_ptr` n'a aucune donnée membre ou fonction membre publique.

### <a name="comparisons"></a>Comparaisons

Vous pouvez utiliser les opérateurs égal (`==`) et non égal (`!=`) pour comparer deux objets `exception_ptr`. Les opérateurs ne comparent pas la valeur binaire (modèle binaire) des structures `EXCEPTION_RECORD` qui représentent les exceptions. À la place, les opérateurs comparent les adresses dans le domaine de référence d'exception des objets `exception_ptr`. Par conséquent, une exception `exception_ptr` null et la valeur NULL sont considérées comme égales.

## <a name="current_exception-function"></a>current_exception function

Call the `current_exception` function in a **catch** block. If an exception is in flight and the **catch** block can catch the exception, the `current_exception` function returns an `exception_ptr` object that references the exception. Sinon, la fonction retourne un objet `exception_ptr` null.

### <a name="details"></a>Détails

The `current_exception` function captures the exception that is in flight regardless of whether the **catch** statement specifies an [exception-declaration](../cpp/try-throw-and-catch-statements-cpp.md) statement.

The destructor for the current exception is called at the end of the **catch** block if you do not rethrow the exception. Toutefois, même si vous appelez la fonction `current_exception` dans le destructeur, celle-ci retourne un objet `exception_ptr` qui référence l’exception actuelle.

Les appels successifs à la fonction `current_exception` retournent des objets `exception_ptr` qui font référence à des copies de l'exception actuelle. Par conséquent, les objets sont considérés comme inégaux car ils font référence à des copies, bien que les copies aient la même valeur binaire.

### <a name="seh-exceptions"></a>SEH exceptions

If you use the **/EHa** compiler option, you can catch an SEH exception in a C++ **catch** block. La fonction `current_exception` retourne un objet `exception_ptr` qui référence l'exception SEH. And the `rethrow_exception` function throws the SEH exception if you call it with thetransported `exception_ptr` object as its argument.

The `current_exception` function returns a null `exception_ptr` if you call it in an SEH **__finally** termination handler, an **__except** exception handler, or the **__except** filter expression.

Une exception transportée ne prend pas en charge les exceptions imbriquées. Une exception imbriquée se produit lorsqu'une autre exception est levée pendant la gestion d'une exception. Si vous interceptez une exception imbriquée, les données membres `EXCEPTION_RECORD.ExceptionRecord` pointent vers une chaîne de structures `EXCEPTION_RECORD` qui décrivent les exceptions associées. La fonction `current_exception` ne prend pas en charge les exceptions imbriquées car elle retourne un objet `exception_ptr` dont la donnée membre `ExceptionRecord` est mise à zéro.

Si vous interceptez une exception SEH, vous devez gérer la mémoire référencée par tout pointeur dans le tableau de données membres `EXCEPTION_RECORD.ExceptionInformation`. Vous devez vous assurer que la mémoire est valide pendant la durée de vie de l'objet `exception_ptr` correspondant, et que cette mémoire est libérée lorsque l'objet `exception_ptr` est supprimé.

Vous pouvez utiliser les fonctions de traduction d’exceptions structurées avec la fonctionnalité de transport d’exceptions. Si une exception SEH est traduite en une exception C++, la fonction `current_exception` retourne `exception_ptr` qui référence l'exception traduite au lieu de l'exception SEH originale. La fonction `rethrow_exception` lève ultérieurement l'exception traduite, pas l'exception d'origine. For more information about SE translator functions, see [_set_se_translator](../c-runtime-library/reference/set-se-translator.md).

## <a name="rethrow_exception-function"></a>rethrow_exception function

Après avoir enregistré une exception interceptée dans un objet `exception_ptr`, le thread principal peut traiter l'objet. Dans votre thread principal, appelez la fonction `rethrow_exception` avec l'objet `exception_ptr` en tant qu'argument. La fonction `rethrow_exception` extrait l'exception de l'objet `exception_ptr` puis lève l'exception dans le contexte du thread principal. If the *p* parameter of the `rethrow_exception` function is a null `exception_ptr`, the function throws [std::bad_exception](../standard-library/bad-exception-class.md).

L'exception extraite est maintenant l'exception actuelle dans le thread principal, et vous pouvez la gérer comme n'importe quelle autre exception. If you catch the exception, you can handle it immediately or use a **throw** statement to send it to a higher level exception handler. Sinon, ne faites rien et laissez le gestionnaire d'exceptions systèmes par défaut terminer le processus.

## <a name="make_exception_ptr-function"></a>make_exception_ptr, fonction

La fonction `make_exception_ptr` prend une instance de classe comme argument puis retourne un `exception_ptr` qui référence l'instance. Généralement, vous spécifiez un objet de [classe exception](../standard-library/exception-class.md) comme argument pour la fonction `make_exception_ptr`, bien que tout objet de classe puisse être l’argument.

Calling the `make_exception_ptr` function is equivalent to throwing a C++ exception, catching it in a **catch** block, and then calling the `current_exception` function to return an `exception_ptr` object that references the exception. L'implémentation Microsoft de la fonction `make_exception_ptr` est plus efficace que le fait de lever puis d'intercepter une exception.

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

## <a name="requirements"></a>spécifications

**En-tête :** \<exception>

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../cpp/exception-handling-in-visual-cpp.md)<br/>
[/EH (Modèle de gestion des exceptions)](../build/reference/eh-exception-handling-model.md)<br/>
[/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md)
