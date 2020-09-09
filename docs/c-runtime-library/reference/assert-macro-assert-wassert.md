---
title: assert (macro), _assert, _wassert
description: Effets des macros et des fonctions Assert dans le runtime C.
ms.date: 11/04/2016
api_name:
- assert
- _assert
- _wassert
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- assert
- _assert
- _wassert
- assert/_wassert
helpviewer_keywords:
- aborting programs
- assert function
- assert macro
ms.assetid: a9ca031a-648b-47a6-bdf1-65fc7399dd40
ms.openlocfilehash: 071424f2201ceda43438fe1056801811fe444a01
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609081"
---
# <a name="assert-macro-_assert-_wassert"></a>assert (macro), _assert, _wassert

Évalue une expression et, lorsque le résultat est **`false`** , imprime un message de diagnostic et abandonne le programme.

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

*expression*<br/>
Expression scalaire (y compris les expressions de pointeur) qui prend la valeur différente de zéro ( **`true`** ) ou 0 ( **`false`** ).

*message*<br/>
Message à afficher.

*extension*<br/>
Nom du fichier source où l’assertion a échoué.

*line*<br/>
Numéro de ligne dans le fichier source de l’assertion ayant échoué.

## <a name="remarks"></a>Notes

La macro `assert` sert généralement à identifier les erreurs de logique pendant le développement de programme. Utilisez-le pour arrêter l’exécution du programme lorsque des conditions inattendues se produisent en implémentant l’argument d' *expression* pour évaluer à **`false`** uniquement lorsque le programme ne fonctionne pas correctement. Les vérifications d’assertion peuvent être désactivées au moment de la compilation en définissant la macro **NDEBUG**. Vous pouvez désactiver la macro `assert` sans modifier vos fichiers source à l’aide de l’option de ligne de commande **/DNDEBUG** . Vous pouvez désactiver la `assert` macro dans votre code source en utilisant une `#define NDEBUG` directive avant que \<assert.h> ne soit inclus.

La `assert` macro imprime un message de diagnostic lorsque l' *expression* correspond à **`false`** (0) et appelle [`abort`](abort.md) pour arrêter l’exécution du programme. Aucune action n’est effectuée si l' *expression* est **`true`** (différente de zéro). Le message de diagnostic contient l'expression qui a échoué, le nom du fichier source et le numéro de ligne où l'assertion a échoué.

Le message de diagnostic est imprimé en caractères larges ( `wchar_t` ). Par conséquent, elle fonctionnera comme prévu, même si l’expression contient des caractères Unicode.

La destination du message de diagnostic dépend du type d'application qui a appelé la routine. Les applications console reçoivent le message via **stderr**. Dans une application Windows, `assert` appelle la fonction Windows [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) pour créer une boîte de message pour afficher le message avec trois boutons : **abandonner**, **Réessayer**et **Ignorer**. Si l'utilisateur clique sur **Abandonner**, le programme s'interrompt immédiatement. Si l'utilisateur clique sur **Réessayer**, le débogueur est appelé et l'utilisateur peut déboguer le programme si le débogage juste-à-temps (JIT) est activé. Si l’utilisateur clique sur **Ignorer**, le programme continue de s’exécuter normalement. Le fait de cliquer sur **Ignorer** lorsqu’une condition d’erreur existe peut entraîner un comportement indéfini, car les conditions préalables du code appelant n’ont pas été remplies.

Pour remplacer le comportement de sortie par défaut quel que soit le type d’application, appelez [`_set_error_mode`](set-error-mode.md) pour choisir entre le comportement de boîte de dialogue de sortie à stderr et d’affichage.

Une fois que `assert` affiche son message, il appelle [`abort`](abort.md) , qui affiche une boîte de dialogue avec les boutons  **abandonner**, **Réessayer**et **Ignorer** . [`abort`](abort.md) quitte le programme. par conséquent, le bouton **Réessayer** et **Ignorer** ne reprendra pas l’exécution du programme après l' `assert` appel. Si `assert` une boîte de dialogue s’affiche, la [`abort`](abort.md) boîte de dialogue n’est pas affichée. La seule fois où la [`abort`](abort.md) boîte de dialogue s’affiche lorsque `assert` envoie sa sortie vers stderr.

En raison du comportement ci-dessus, une boîte de dialogue s’affiche toujours à la suite d’un `assert` appel en mode débogage. Le comportement de chaque bouton est capturé dans le tableau ci-dessous.

|Mode d’erreur|Sortie vers stderr (console/_OUT_TO_STDERR)|Boîte de dialogue Afficher (Windows/_OUT_TO_MSGBOX)|
|----------|----------------|------------------|
|Abandon|Quitter immédiatement avec le code de sortie 3|Quitter immédiatement avec le code de sortie 3|
|Recommencer|Arrêter dans le débogueur pendant `abort`|Arrêter dans le débogueur pendant `assert`|
|Ignorer|Terminer la sortie via `abort`|Continuer le programme comme si l’assertion n’avait pas été déclenchée (peut entraîner un comportement indéfini dans la mesure où les conditions préalables du code appelant n’ont pas été remplies)|

Pour plus d’informations sur le débogage CRT, consultez [Techniques de débogage CRT](/visualstudio/debugger/crt-debugging-techniques).

Les fonctions `_assert` et `_wassert` sont des fonctions CRT internes. Elles aident à réduire la quantité de code nécessaire dans vos fichiers objet pour prendre en charge les assertions. Nous vous déconseillons d’appeler ces fonctions directement.

La `assert` macro est activée dans les versions release et Debug des bibliothèques Runtime C lorsque **NDEBUG** n’est pas défini. Lorsque **NDEBUG** est défini, la macro est disponible mais n’évalue pas son argument et n’a aucun effet. Lorsqu’elle est activée, la `assert` macro appelle `_wassert` pour son implémentation. D’autres macros d’assertion, [_ASSERT](assert-asserte-assert-expr-macros.md), [_ASSERTE](assert-asserte-assert-expr-macros.md) et [_ASSERT_EXPR](assert-asserte-assert-expr-macros.md), sont également disponibles, mais elles évaluent seulement les expressions qui leur sont passées quand la macro [_DEBUG](../../c-runtime-library/debug.md) a été définie et quand elles sont dans du code lié à la version Debug des bibliothèques Runtime C.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|`assert`, `_wassert`|\<assert.h>|

La signature de la `_assert` fonction n’est pas disponible dans un fichier d’en-tête. La signature de la `_wassert` fonction n’est disponible que lorsque la macro **NDEBUG** n’est pas définie.

## <a name="example"></a>Exemple

Dans ce programme, la fonction **analyze_string** utilise la `assert` macro pour tester plusieurs conditions liées à la chaîne et à la longueur. Si l'une des conditions échoue, le programme envoie un message indiquant la cause de l'échec.

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

Après l’échec de l’assertion, en fonction de la version du système d’exploitation et de la bibliothèque Runtime, vous pouvez voir une boîte de message qui contient un nom similaire à ce qui suit :

```Output
A problem caused the program to stop working correctly. Windows will close the program and notify you if a solution is available.
```

Si un débogueur est installé, sélectionnez le bouton **Déboguer** pour démarrer le débogueur, ou **Fermer le programme** pour quitter.

## <a name="see-also"></a>Voir aussi

[Gestion des erreurs](../../c-runtime-library/error-handling-crt.md)<br/>
[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[génère](raise.md)<br/>
[signal](signal.md)<br/>
[_ASSERT, _ASSERTE _ASSERT_EXPR macros](assert-asserte-assert-expr-macros.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
