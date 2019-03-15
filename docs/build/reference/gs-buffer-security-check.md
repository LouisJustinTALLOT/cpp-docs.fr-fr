---
title: /GS (vérification de la sécurité des mémoires tampons)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BufferSecurityCheck
- VC.Project.VCCLCompilerTool.BufferSecurityCheck
- /GS
helpviewer_keywords:
- buffers [C++], buffer overruns
- buffer overruns, compiler /GS switch
- GS compiler option [C++]
- /GS compiler option [C++]
- security check compiler option [C++]
- -GS compiler option [C++]
- buffers [C++], avoiding overruns
ms.assetid: 8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e
ms.openlocfilehash: 10afa874092eb563903ba5f49c6add136afc869c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820232"
---
# <a name="gs-buffer-security-check"></a>/GS (vérification de la sécurité des mémoires tampons)

Détecte des dépassements de mémoire tampon qui remplacent l’adresse de retour d’une fonction, adresse du Gestionnaire d’exception ou certains types de paramètres. À l’origine d’un dépassement de mémoire tampon est une technique utilisée par les pirates pour exploiter le code qui n’applique pas les restrictions de taille de mémoire tampon.

## <a name="syntax"></a>Syntaxe

```
/GS[-]
```

## <a name="remarks"></a>Notes

**/GS** est activée par défaut. Si vous pensez que votre application de n’avoir aucun risque pour la sécurité, utilisez **/GS-**. Pour plus d’informations sur la détection de dépassement de mémoire tampon de suppression, consultez [safebuffers](../../cpp/safebuffers.md).

## <a name="security-checks"></a>Vérifications de sécurité

Sur les fonctions que le compilateur reconnaît comme sujets à des problèmes de dépassement de mémoire tampon, le compilateur alloue de l’espace sur la pile avant l’adresse de retour. À l’entrée de fonction, l’espace alloué est chargé avec un *cookie de sécurité* qui est calculée une fois au moment du chargement du module. Sur la sortie de la fonction et pendant le déroulement de frame sur les systèmes d’exploitation 64 bits, une fonction d’assistance est appelée pour vous assurer que la valeur du cookie est toujours la même. Une autre valeur indique qu’un remplacement de la pile peut se sont produites. Si une valeur différente est détectée, le processus est terminé.

## <a name="gs-buffers"></a>Mémoires tampon GS

Une vérification de sécurité de dépassement de mémoire tampon est effectuée sur un *mémoire tampon GS*. Une mémoire tampon GS peut être une d’elles :

- Un tableau qui est supérieure à 4 octets, a plus de deux éléments et a un type d’élément qui n’est pas un type pointeur.

- Structure de données dont la taille est supérieure à 8 octets et contient pas de pointeurs.

- Une mémoire tampon alloué à l’aide de la [_alloca](../../c-runtime-library/reference/alloca.md) (fonction).

- Toute classe ou une structure qui contient une mémoire tampon GS.

Par exemple, les instructions suivantes déclarent des mémoires tampon GS.

```cpp
char buffer[20];
int buffer[20];
struct { int a; int b; int c; int d; } myStruct;
struct { int a; char buf[20]; };
```

Toutefois, les instructions suivantes ne déclarent pas les mémoires tampon GS. Les deux premières déclarations contiennent des éléments de type pointeur. Les troisième et quatrième instructions déclarent des tableaux dont la taille est trop petite. La cinquième instruction déclare une structure dont la taille sur un x86 plateforme n’est pas plus de 8 octets.

```cpp
char *pBuf[20];
void *pv[20];
char buf[4];
int buf[2];
struct { int a; int b; };
```

## <a name="initialize-the-security-cookie"></a>Initialiser le Cookie de sécurité

Le **/GS** option du compilateur nécessite que le cookie de sécurité soit initialisée avant l’exécution de n’importe quelle fonction qui utilise le cookie. Le cookie de sécurité doit être initialisé immédiatement sur ENTRÉE pour un EXE ou DLL. Cette opération est automatique si vous utilisez les points d’entrée par défaut VCRuntime : mainCRTStartup, wmainCRTStartup, WinMainCRTStartup, wWinMainCRTStartup, ou _DllMainCRTStartup. Si vous utilisez un autre point d’entrée, vous devez initialiser manuellement le cookie de sécurité en appelant [__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md).

## <a name="what-is-protected"></a>Ce qui est protégé

Le **/GS** option du compilateur protège les éléments suivants :

- L’adresse de retour d’un appel de fonction.

- L’adresse d’un gestionnaire d’exceptions pour une fonction.

- Paramètres de fonction vulnérables.

Sur toutes les plateformes, **/GS** essaie de détecter les saturations de mémoire tampon dans l’adresse de retour. Dépassements de mémoire tampon sont plus facilement exploitées sur les plateformes telles que x86 et x64, qui utilisent des conventions d’appel qui stockent l’adresse de retour d’un appel de fonction sur la pile.

Sur x86, si une fonction utilise un gestionnaire d’exceptions, le compilateur injecte un cookie de sécurité pour protéger l’adresse du Gestionnaire d’exceptions. Le cookie est vérifié pendant le déroulement de frame.

**/GS** protège *paramètres vulnérables* qui sont passés dans une fonction. Un paramètre vulnérable est un pointeur, une référence C++, une C-structure (type POD C++) qui contient un pointeur ou une mémoire tampon GS.

Un paramètre vulnérable est alloué avant le cookie et les variables locales. Un dépassement de mémoire tampon peut remplacer ces paramètres. Et code de la fonction qui utilise ces paramètres peut provoquer une attaque avant que la fonction retourne et la vérification de sécurité est effectuée. Pour limiter ce risque, le compilateur effectue une copie des paramètres vulnérables pendant le prologue de fonction et les place sous la zone de stockage pour les mémoires tampons.

Le compilateur ne fait pas de copies de paramètres vulnérables dans les situations suivantes :

- Fonctions qui ne contiennent pas d’une mémoire tampon GS.

- Optimisations ([/O options](o-options-optimize-code.md)) ne sont pas activés.

- Fonctions qui ont une liste d’arguments variable (...).

- Fonctions qui sont marquées avec [naked](../../cpp/naked-cpp.md).

- Fonctions qui contiennent le code assembleur inline dans la première instruction.

- Un paramètre est utilisé uniquement dans les méthodes qui sont moins susceptibles d’être exploitable en cas d’un dépassement de mémoire tampon.

## <a name="what-is-not-protected"></a>Ce qui n’est pas protégé.

Le **/GS** option du compilateur ne protège pas contre toutes les attaques de sécurité de dépassement de mémoire tampon. Par exemple, si vous avez une mémoire tampon et un vtable dans un objet, un dépassement de mémoire tampon peut endommager le vtable.

Même si vous utilisez **/GS**, essayez toujours d’écrire du code sécurisé qui n’a aucun dépassements de mémoire tampon.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Pour définir cette option de compilateur dans Visual Studio

1. Dans **l’Explorateur de solutions**, cliquez sur le projet, puis cliquez sur **propriétés**.

   Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Dans le **Pages de propriétés** boîte de dialogue, cliquez sur le **C/C++** dossier.

1. Cliquez sur le **génération de Code** page de propriétés.

1. Modifier le **Buffer Security Check** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BufferSecurityCheck%2A>.

## <a name="example"></a>Exemple

Cet exemple les saturations de mémoire tampon. Cela entraîne l’échec lors de l’exécution de l’application.

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
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
