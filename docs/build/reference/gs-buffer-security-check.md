---
description: En savoir plus sur:/GS (vérification de la sécurité des tampons)
title: /GS (vérification de la sécurité des mémoires tampons)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BufferSecurityCheck
- VC.Project.VCCLCompilerTool.BufferSecurityCheck
helpviewer_keywords:
- buffers [C++], buffer overruns
- buffer overruns, compiler /GS switch
- GS compiler option [C++]
- /GS compiler option [C++]
- security check compiler option [C++]
- -GS compiler option [C++]
- buffers [C++], avoiding overruns
ms.assetid: 8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e
ms.openlocfilehash: 4d7fa3c2220260914c9ff931c2f2e7c76bf12ea1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191873"
---
# <a name="gs-buffer-security-check"></a>/GS (vérification de la sécurité des mémoires tampons)

Détecte des dépassements de mémoire tampon qui remplacent l’adresse de retour d’une fonction, l’adresse du gestionnaire d’exceptions ou certains types de paramètres. Provoquer un dépassement de mémoire tampon est une technique utilisée par les pirates pour exploiter du code qui n’applique pas les restrictions de taille de mémoire tampon.

## <a name="syntax"></a>Syntaxe

```
/GS[-]
```

## <a name="remarks"></a>Notes

**/GS** est activé par défaut. Si vous vous attendez à ce que votre application n’ait aucune exposition de sécurité, utilisez **/GS-**. Pour plus d’informations sur la suppression de la détection de dépassement de mémoire tampon, consultez [safebuffers](../../cpp/safebuffers.md).

## <a name="security-checks"></a>Vérifications de sécurité

Sur les fonctions que le compilateur reconnaît comme sujettes à des problèmes de dépassement de mémoire tampon, le compilateur alloue de l’espace sur la pile avant l’adresse de retour. Dans l’entrée de la fonction, l’espace alloué est chargé avec un *cookie de sécurité* qui est calculé une fois lors du chargement du module. Sur la sortie de la fonction, et Pendant le déroulement du frame sur les systèmes d’exploitation 64 bits, une fonction d’assistance est appelée pour s’assurer que la valeur du cookie est toujours la même. Une valeur différente indique qu’un remplacement de la pile s’est peut-être produit. Si une autre valeur est détectée, le processus se termine.

## <a name="gs-buffers"></a>Mémoires tampons GS

Une vérification de la sécurité de dépassement de mémoire tampon est effectuée sur une *mémoire tampon GS*. Une mémoire tampon GS peut être l’une des suivantes :

- Tableau de plus de 4 octets, ayant plus de deux éléments et ayant un type d’élément qui n’est pas un type pointeur.

- Structure de données dont la taille est supérieure à 8 octets et ne contient pas de pointeurs.

- Mémoire tampon allouée à l’aide de la fonction [_alloca](../../c-runtime-library/reference/alloca.md) .

- Toute classe ou structure qui contient une mémoire tampon GS.

Par exemple, les instructions suivantes déclarent des mémoires tampons GS.

```cpp
char buffer[20];
int buffer[20];
struct { int a; int b; int c; int d; } myStruct;
struct { int a; char buf[20]; };
```

Toutefois, les instructions suivantes ne déclarent pas de mémoires tampons GS. Les deux premières déclarations contiennent des éléments de type pointeur. Les troisième et quatrième instructions déclarent des tableaux dont la taille est trop petite. La cinquième instruction déclare une structure dont la taille sur une plateforme x86 n’est pas supérieure à 8 octets.

```cpp
char *pBuf[20];
void *pv[20];
char buf[4];
int buf[2];
struct { int a; int b; };
```

## <a name="initialize-the-security-cookie"></a>Initialiser le cookie de sécurité

L’option de compilateur **/GS** requiert l’initialisation du cookie de sécurité avant l’exécution d’une fonction qui utilise le cookie. Le cookie de sécurité doit être initialisé immédiatement à l’entrée dans un fichier EXE ou une DLL. Cela s’effectue automatiquement si vous utilisez les points d’entrée VCRuntime par défaut : mainCRTStartup, wmainCRTStartup, WinMainCRTStartup, wWinMainCRTStartup ou _DllMainCRTStartup. Si vous utilisez un autre point d’entrée, vous devez initialiser manuellement le cookie de sécurité en appelant [__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md).

## <a name="what-is-protected"></a>Ce qui est protégé

L’option de compilateur **/GS** protège les éléments suivants :

- Adresse de retour d’un appel de fonction.

- Adresse d’un gestionnaire d’exceptions pour une fonction.

- Paramètres de fonction vulnérables.

Sur toutes les plateformes, **/GS** tente de détecter les dépassements de mémoire tampon dans l’adresse de retour. Les dépassements de mémoire tampon sont plus faciles à exploiter sur les plateformes telles que x86 et x64, qui utilisent des conventions d’appel qui stockent l’adresse de retour d’un appel de fonction sur la pile.

Sur x86, si une fonction utilise un gestionnaire d’exceptions, le compilateur injecte un cookie de sécurité pour protéger l’adresse du gestionnaire d’exceptions. Le cookie est vérifié pendant le déroulement du frame.

**/GS** protège les *paramètres vulnérables* passés dans une fonction. Un paramètre vulnérable est un pointeur, une référence C++, une structure C (type POD C++) qui contient un pointeur ou une mémoire tampon GS.

Un paramètre vulnérable est alloué avant le cookie et les variables locales. Un dépassement de mémoire tampon peut remplacer ces paramètres. Et le code de la fonction qui utilise ces paramètres peut provoquer une attaque avant que la fonction ne retourne et que la vérification de sécurité soit effectuée. Pour réduire ce risque, le compilateur effectue une copie des paramètres vulnérables pendant le prologue des fonctions et les met en dessous de la zone de stockage pour toutes les mémoires tampons.

Le compilateur n’effectue pas de copies des paramètres vulnérables dans les cas suivants :

- Fonctions qui ne contiennent pas de mémoire tampon GS.

- Les optimisations ([options/o](o-options-optimize-code.md)) ne sont pas activées.

- Fonctions qui ont une liste d’arguments de variables (...).

- Fonctions marquées avec [Naked](../../cpp/naked-cpp.md).

- Fonctions qui contiennent du code assembleur inline dans la première instruction.

- Un paramètre est utilisé uniquement de manière moins susceptible d’être exploitable en cas de dépassement de mémoire tampon.

## <a name="what-is-not-protected"></a>Ce qui n’est pas protégé

L’option de compilateur **/GS** ne protège pas contre toutes les attaques de sécurité de dépassement de mémoire tampon. Par exemple, si vous avez une mémoire tampon et un vtable dans un objet, un dépassement de mémoire tampon peut corrompre la vtable.

Même si vous utilisez **/GS**, essayez toujours d’écrire du code sécurisé qui n’a pas de dépassements de mémoire tampon.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Pour définir cette option de compilateur dans Visual Studio

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis cliquez sur **Propriétés**.

   Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Dans la boîte de dialogue **pages de propriétés** , cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **génération de code** .

1. Modifiez la propriété vérification de la sécurité de la **mémoire tampon** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BufferSecurityCheck%2A>.

## <a name="example"></a>Exemple

Cet exemple exécute une mémoire tampon. Cela provoque l’échec de l’application au moment de l’exécution.

```C
// compile with: /c /W1
#include <cstring>
#include <stdlib.h>
#pragma warning(disable : 4996)   // for strcpy use

// Vulnerable function
void vulnerable(const char *str) {
   char buffer[10];
   strcpy(buffer, str); // overrun buffer !!!

   // use a secure CRT function to help prevent buffer overruns
   // truncate string to fit a 10 byte buffer
   // strncpy_s(buffer, _countof(buffer), str, _TRUNCATE);
}

int main() {
   // declare buffer that is bigger than expected
   char large_buffer[] = "This string is longer than 10 characters!!";
   vulnerable(large_buffer);
}
```

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
