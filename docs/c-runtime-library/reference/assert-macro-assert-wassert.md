---
title: assert (macro), _assert, _wassert | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- assert
- _assert
- _wassert
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- assert
- _assert
- _wassert
- assert/_wassert
dev_langs:
- C++
helpviewer_keywords:
- aborting programs
- assert function
- assert macro
ms.assetid: a9ca031a-648b-47a6-bdf1-65fc7399dd40
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0318abde877e9b647c1781408d2e22cc9d70824e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397839"
---
# <a name="assert-macro-assert-wassert"></a>assert (macro), _assert, _wassert

Évalue une expression et, lorsque le résultat est **false**, imprime un message de diagnostic et interrompt le programme.

## <a name="syntax"></a>Syntaxe

```C
assert(
   expression
);
void _assert(
   char const* message,
   char const* filename,
   unsigned line
);
void _wassert(
   wchar_t const* message,
   wchar_t const* filename,
   unsigned line
);
```

### <a name="parameters"></a>Paramètres

*expression* une expression scalaire (expressions de pointeur comprises) qui prend la valeur de différente de zéro (**true**) ou 0 (**false**).

*message* le message à afficher.

*nom de fichier* l’assertion a échoué dans le nom de la source du fichier.

*ligne* le numéro de ligne dans le fichier source de l’échec d’assertion.

## <a name="remarks"></a>Notes

Le **assert** macro est généralement utilisé pour identifier des erreurs de logique pendant le développement de programme. Il permet d’arrêter l’exécution du programme lorsque des conditions inattendues se produisent en implémentant la *expression* argument soit évaluée comme **false** uniquement lorsque le programme fonctionne correctement. Contrôles d’assertion peuvent être désactivées au moment de la compilation en définissant la macro **NDEBUG**. Vous pouvez désactiver le **assert** macro sans modifier vos fichiers source à l’aide un **/DNDEBUG** une option de ligne de commande. Vous pouvez désactiver le **assert** macro dans votre code source en utilisant un `#define NDEBUG` directive avant \<assert.h > est inclus.

Le **assert** imprime macro un message de diagnostic lorsque *expression* prend la valeur de **false** (0) et appelle [abandonner](abort.md) pour arrêter le programme exécution. Aucune action n’est effectuée si *expression* est **true** (différente de zéro). Le message de diagnostic contient l'expression qui a échoué, le nom du fichier source et le numéro de ligne où l'assertion a échoué.

le message de diagnostic est imprimé en caractères larges. Ainsi, la procédure fonctionne comme prévu même si l'expression contient des caractères Unicode.

La destination du message de diagnostic dépend du type d'application qui a appelé la routine. Applications console reçoivent toujours le message via **stderr**. Dans une application Windows, **assert** appelle Windows [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) fonction permettant de créer une boîte de message pour afficher le message avec un **OK** bouton. Lorsque l'utilisateur clique sur **OK**, le programme s'interrompt immédiatement.

Lorsque l’application est liée à une version debug des bibliothèques Runtime, **assert** crée une boîte de message avec trois boutons : **abandonner**, **réessayer**et **Ignorer**. Si l'utilisateur clique sur **Abandonner**, le programme s'interrompt immédiatement. Si l'utilisateur clique sur **Réessayer**, le débogueur est appelé et l'utilisateur peut déboguer le programme si le débogage juste-à-temps (JIT) est activé. Si l’utilisateur clique sur **ignorer**, **assert** poursuit son exécution normale : création de la boîte de message avec le **OK** bouton. Notez que lorsque vous cliquez sur **Ignorer** alors qu'une condition d'erreur existe, un comportement non défini peut se produire.

Pour plus d'informations sur le débogage CRT, consultez [Techniques de débogage CRT](/visualstudio/debugger/crt-debugging-techniques).

Le **_assert** et **_wassert** fonctions sont les fonctions CRT internes. Elles aident à réduire la quantité de code nécessaire dans vos fichiers objet pour prendre en charge les assertions. Nous vous déconseillons d’appeler ces fonctions directement.

Le **assert** (macro) est activé dans les versions release et debug des bibliothèques Runtime C lorsque **NDEBUG** n’est pas défini. Lorsque **NDEBUG** est défini, la macro est disponible mais n’évalue pas son argument et n’a aucun effet. Lorsqu’elle est activée, le **assert** appels de macros **_wassert** pour son implémentation. D’autres macros d’assertion, [_ASSERT](assert-asserte-assert-expr-macros.md), [_ASSERTE](assert-asserte-assert-expr-macros.md) et [_ASSERT_EXPR](assert-asserte-assert-expr-macros.md), sont également disponibles, mais elles évaluent seulement les expressions qui leur sont passées quand la macro [_DEBUG](../../c-runtime-library/debug.md) a été définie et quand elles sont dans du code lié à la version Debug des bibliothèques Runtime C.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**Assert**, **_wassert**|\<assert.h>|

La signature de la **_assert** fonction n’est pas disponible dans un fichier d’en-tête. La signature de la **_wassert** fonction est disponible uniquement lorsque le **NDEBUG** macro n’est pas définie.

## <a name="example"></a>Exemple

Dans ce programme, le **analyze_string** fonction utilise le **assert** macro pour tester plusieurs conditions liées à la longueur et de la chaîne. Si l'une des conditions échoue, le programme envoie un message indiquant la cause de l'échec.

```C
// crt_assert.c
// compile by using: cl /W4 crt_assert.c
#include <stdio.h>
#include <assert.h>
#include <string.h>

void analyze_string( char *string );   // Prototype

int main( void )
{
   char  test1[] = "abc", *test2 = NULL, test3[] = "";

   printf ( "Analyzing string '%s'\n", test1 ); fflush( stdout );
   analyze_string( test1 );
   printf ( "Analyzing string '%s'\n", test2 ); fflush( stdout );
   analyze_string( test2 );
   printf ( "Analyzing string '%s'\n", test3 ); fflush( stdout );
   analyze_string( test3 );
}

// Tests a string to see if it is NULL,
// empty, or longer than 0 characters.
void analyze_string( char * string )
{
   assert( string != NULL );        // Cannot be NULL
   assert( *string != '\0' );       // Cannot be empty
   assert( strlen( string ) > 2 );  // Length must exceed 2
}
```

Le programme génère cette sortie :

```Output
Analyzing string 'abc'
Analyzing string '(null)'
Assertion failed: string != NULL, file crt_assert.c, line 25
```

Après l’échec d’assertion, en fonction de la version du système d’exploitation et de la bibliothèque Runtime, vous pouvez voir une boîte de message contenant du texte semblable à celui-ci :

```Output
A problem caused the program to stop working correctly. Windows will close the program and notify you if a solution is available.
```

Si un débogueur est installé, sélectionnez le bouton **Déboguer** pour démarrer le débogueur, ou **Fermer le programme** pour quitter.

## <a name="see-also"></a>Voir aussi

[Gestion des erreurs](../../c-runtime-library/error-handling-crt.md)<br/>
[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[raise](raise.md)<br/>
[signal](signal.md)<br/>
[_ASSERT, _ASSERTE, _ASSERT_EXPR, macros](assert-asserte-assert-expr-macros.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
