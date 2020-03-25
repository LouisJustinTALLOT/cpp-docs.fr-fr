---
title: Avertissement des outils Éditeur de liens LNK4049
ms.date: 04/15/2019
f1_keywords:
- LNK4049
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
ms.openlocfilehash: a8e4416eafd47f584de4ab1c83aa7303cab0440a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194133"
---
# <a name="linker-tools-warning-lnk4049"></a>Avertissement des outils Éditeur de liens LNK4049

> le symbole'*symbol*'défini dans'*nom_fichier. obj*'est importé

[__declspec (dllimport)](../../cpp/dllexport-dllimport.md) a été spécifié pour *symbol* même si le symbole est défini dans le fichier objet *NomFichier. obj* de la même image. Supprimez le modificateur `__declspec(dllimport)` pour résoudre cet avertissement.

## <a name="remarks"></a>Notes

Cet avertissement est généré par l’éditeur de liens lorsque vous définissez un symbole dans un fichier objet et que vous le référencez à l’aide du modificateur de déclaration `__declspec(dllimport)` dans un autre.

Avertissement LNK4049 est une version plus générale de l' [Avertissement des outils Éditeur de liens LNK4217](linker-tools-warning-lnk4217.md). L’éditeur de liens génère l’avertissement LNK4049 lorsqu’il ne peut pas déterminer la fonction ou le fichier objet référencé par le symbole importé.

Les cas courants où LNK4049 est généré à la place de LNK4217 sont les suivants :

- Lors de l’utilisation de l’option [/INCREMENTAL](../../build/reference/incremental-link-incrementally.md) .

- Lors de l’utilisation de l’option [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) .

Pour résoudre LNK4049, essayez l’une des procédures suivantes :

- Supprimez le modificateur `__declspec(dllimport)` de la déclaration anticipée du symbole qui a déclenché LNK4049. Vous pouvez rechercher des symboles dans une image binaire à l’aide de l’utilitaire **DUMPBIN** . Le commutateur **DUMPBIN/SYMBOLS** affiche la table de symboles COFF de l’image. Pour plus d’informations sur l’utilitaire **DUMPBIN** , consultez [Référence DUMPBIN](../../build/reference/dumpbin-reference.md).

- Désactivez temporairement la liaison incrémentielle et l’optimisation de l’ensemble du programme. Lors de la recompilation, l’application génère un avertissement LNK4217, qui comprend le nom de la fonction qui fait référence au symbole importé. Supprimez le modificateur de déclaration `__declspec(dllimport)` du symbole importé et réactivez l’édition de liens incrémentielle ou l’optimisation de l’ensemble du programme selon les besoins.

Bien que le code généré final se comporte correctement, le code généré pour appeler la fonction importée est moins efficace que l’appel direct de la fonction. Cet avertissement n’apparaît pas quand vous compilez à l’aide de l’option [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) .

Pour plus d’informations sur les déclarations d’importation et d’exportation de données, consultez [dllexport, DllImport](../../cpp/dllexport-dllimport.md).

## <a name="example"></a>Exemple

La liaison des deux modules suivants génère LNK4049. Le premier module génère un fichier objet contenant une seule fonction exportée.

```cpp
// LNK4049a.cpp
// compile with: /c

__declspec(dllexport) int func()
{
   return 3;
}
```

Le deuxième module génère un fichier objet contenant une déclaration anticipée à la fonction exportée dans le premier module, ainsi qu’un appel à cette fonction à l’intérieur de la fonction `main`. La liaison de ce module au premier module générera LNK4049. Supprimez le modificateur `__declspec(dllimport)` de la déclaration pour résoudre l’avertissement.

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

[Avertissement des outils Éditeur de liens LNK4217](linker-tools-warning-lnk4217.md) \
[Avertissement des outils Éditeur de liens LNK4286](linker-tools-warning-lnk4286.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)
