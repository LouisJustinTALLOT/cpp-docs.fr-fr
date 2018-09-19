---
title: Avertissement LNK4049 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4049
dev_langs:
- C++
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ad4e4adb492789639c71a25a2db774a80cd77c9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021757"
---
# <a name="linker-tools-warning-lnk4049"></a>Avertissement des outils Éditeur de liens LNK4049

symbole 'symbole' importé défini localement

Le symbole a été exporté à partir d’et importé dans le programme.

Cet avertissement est généré par l’éditeur de liens lorsque vous déclarez un symbole à l’aide de la `__declspec(dllexport)` attribut dans le fichier d’un objet de classe de stockage et font référence à l’aide de la `__declspec(dllimport)` attribut dans un autre.

Avertissement LNK4049 est une version plus générale de [avertissement d’outils de l’éditeur de liens LNK4217](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md). L’éditeur de liens génère l’avertissement LNK4049 lorsqu’il ne peut pas déterminer de quelle fonction le symbole importé a été référencé.

Les cas courants où LNK4049 est généré au lieu de LNK4217 sont :

- Exécution d’une liaison incrémentielle à l’aide de la [/INCREMENTAL](../../build/reference/incremental-link-incrementally.md) option.

- Exécution d’optimisation de la totalité du programme à l’aide de la [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) option.

Pour résoudre l’erreur LNK4049, essayez l’une des opérations suivantes :

- Supprimer le `__declspec(dllimport)` déclaration à partir de la déclaration anticipée du symbole qui a déclenché LNK4049 de nom. Vous pouvez rechercher les symboles au sein d’une image binaire à l’aide de la **DUMPBIN** utilitaire. Le **DUMPBIN/symboles** commutateur affiche la table de symboles COFF de l’image. Pour plus d’informations sur la **DUMPBIN** utilitaire, consultez [Référence DUMPBIN](../../build/reference/dumpbin-reference.md).

- Désactiver temporairement la liaison incrémentielle et l’optimisation de la totalité du programme. Recompiler l’application génère l’avertissement LNK4217, qui inclut le nom de la fonction à partir de laquelle le symbole importé a été référencé. Supprimer le `__declspec(dllimport)` déclaration de symbole importé et activer la liaison incrémentielle ou l’optimisation de la totalité du programme comme requis.

Bien que le code final généré se comporte correctement, le code généré pour appeler la fonction importée est moins efficace que l’appel de la fonction directement. Cet avertissement n’apparaît pas lorsque vous compilez en utilisant l’option [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

Pour plus d’informations sur Importer et exporter des déclarations de données, consultez [dllexport, dllimport](../../cpp/dllexport-dllimport.md).

## <a name="example"></a>Exemple

Liaison des deux modules suivants génère LNK4049. Le premier module génère un fichier objet qui contient une seule fonction exportée.

```
// LNK4049a.cpp
// compile with: /c

__declspec(dllexport) int func()
{
   return 3;
}
```

## <a name="example"></a>Exemple

Le deuxième module génère un fichier objet qui contient une déclaration anticipée à la fonction exportée dans le premier module, ainsi que d’un appel à cette fonction à l’intérieur de la `main` (fonction). La liaison de ce module avec le premier module génère LNK4049. Suppression de la `__declspec(dllimport)` déclaration peut résoudre l’avertissement.

```
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

[Avertissement des outils Éditeur de liens LNK4217](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)