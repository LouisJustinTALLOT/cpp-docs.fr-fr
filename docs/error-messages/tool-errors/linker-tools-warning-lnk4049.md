---
title: Avertissement des outils Éditeur de liens LNK4049
ms.date: 04/09/2019
f1_keywords:
- LNK4049
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
ms.openlocfilehash: 357bf5a981dddadfd79d2d6981ccc9c478909097
ms.sourcegitcommit: 0ad3f4517e64900a2702dd3d366586f9e2bce2c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/10/2019
ms.locfileid: "59477351"
---
# <a name="linker-tools-warning-lnk4049"></a>Avertissement des outils Éditeur de liens LNK4049

> symbole '*symbole*'définie dans'*filename.obj*' est importé

Le symbole a été exporté à partir d’et importé dans le programme.

Cet avertissement est généré par l’éditeur de liens lorsque vous définissez un symbole dans un fichier objet et faire référence à l’aide de la `__declspec(dllimport)` modificateur de déclaration dans un autre.

Avertissement LNK4049 est une version plus générale de [avertissement d’outils de l’éditeur de liens LNK4217](linker-tools-warning-lnk4217.md). L’éditeur de liens génère l’avertissement LNK4049 lorsqu’il ne peut pas déterminer quel fichier de la fonction ou l’objet référencé le symbole importé.

Les cas courants où LNK4049 est généré au lieu de LNK4217 sont :

- Lorsque vous utilisez le [/INCREMENTAL](../../build/reference/incremental-link-incrementally.md) option.

- Lorsque vous utilisez le [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) option.

Pour résoudre l’erreur LNK4049, essayez l’une des procédures suivantes :

- Supprimer le `__declspec(dllimport)` modificateur à partir de la déclaration anticipée du symbole qui a déclenché LNK4049. Vous pouvez rechercher les symboles au sein d’une image binaire à l’aide de la **DUMPBIN** utilitaire. Le **DUMPBIN /SYMBOLS** commutateur affiche la table de symboles COFF de l’image. Pour plus d’informations sur la **DUMPBIN** utilitaire, consultez [Référence DUMPBIN](../../build/reference/dumpbin-reference.md).

- Désactiver temporairement la liaison incrémentielle et l’optimisation de la totalité du programme. Lors de la recompilation, l’application génère l’avertissement LNK4217, lequel inclut le nom de la fonction qui référence le symbole importé. Supprimer le `__declspec(dllimport)` modificateur de déclaration symbole importé et réactiver la liaison incrémentielle ou l’optimisation de la totalité du programme comme requis.

Bien que le code final généré se comporte correctement, le code généré pour appeler la fonction importée est moins efficace que l’appel de la fonction directement. Cet avertissement n’apparaît pas quand vous compilez à l’aide de la [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) option.

Pour plus d’informations sur Importer et exporter des déclarations de données, consultez [dllexport, dllimport](../../cpp/dllexport-dllimport.md).

## <a name="example"></a>Exemple

Liaison des deux modules suivants génère LNK4049. Le premier module génère un fichier objet qui contient une seule fonction exportée.

```cpp
// LNK4049a.cpp
// compile with: /c

__declspec(dllexport) int func()
{
   return 3;
}
```

Le deuxième module génère un fichier objet qui contient une déclaration anticipée à la fonction exportée dans le premier module, ainsi que d’un appel à cette fonction à l’intérieur de la `main` (fonction). La liaison de ce module avec le premier module génère LNK4049. Supprimer le `__declspec(dllimport)` modificateur de la déclaration de résoudre l’avertissement.

```cpp
// LNK4049b.cpp
// compile with: /link /WX /LTCG LNK4049a.obj
// LNK4049 expected

__declspec(dllimport) int func();
// try the following line instead
// int func();

int main()
{
   return func();
}
```

## <a name="see-also"></a>Voir aussi

[Outils de l’éditeur de liens LNK4217 d’avertissement](linker-tools-warning-lnk4217.md) \
[Avertissement LNK4286 des outils de l’éditeur de liens](linker-tools-warning-lnk4286.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)