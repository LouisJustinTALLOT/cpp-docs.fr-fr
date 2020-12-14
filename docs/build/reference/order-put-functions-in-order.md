---
description: En savoir plus sur:/ORDER (mettre les fonctions dans l’ordre)
title: /ORDER (Mettre les fonctions dans l'ordre)
ms.date: 09/05/2018
f1_keywords:
- VC.Project.VCLinkerTool.FunctionOrder
- /order
helpviewer_keywords:
- ORDER linker option
- -ORDER linker option
- LINK tool [C++], program optimizing
- /ORDER linker option
- LINK tool [C++], swap tuning
- paging, optimizing
ms.assetid: ecf5eb3e-e404-4e86-9a91-4e5ec157261a
ms.openlocfilehash: 36888cbb24c869d06eaaa5830b95ae76fc42b860
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226348"
---
# <a name="order-put-functions-in-order"></a>/ORDER (Mettre les fonctions dans l'ordre)

Spécifiez l’ordre des liens pour les fonctions empaquetées (COMDAT) séparément.

## <a name="syntax"></a>Syntaxe

> **/Order : \@** <em>nom du fichier</em>

### <a name="parameters"></a>Paramètres

*filename*<br/>
Fichier texte qui spécifie l’ordre des liens pour les fonctions COMDAT.

## <a name="remarks"></a>Notes

L’option de compilateur **/Order** vous permet d’optimiser le comportement de pagination de votre programme en regroupant une fonction avec les fonctions qu’elle appelle. Vous pouvez également regrouper les fonctions fréquemment appelées. Ces techniques, appelées *optimisation* de l’échange ou optimisation de la pagination, augmentent la probabilité qu’une fonction *appelée soit en* mémoire lorsqu’elle est nécessaire et qu’elle n’a pas besoin d’être paginée à partir du disque.

Quand vous compilez votre code source dans un fichier objet, vous pouvez indiquer au compilateur de placer chaque fonction dans sa propre section, appelée *COMDAT*, à l’aide de l’option de compilateur [/Gy (activer la liaison au niveau des fonctions)](gy-enable-function-level-linking.md) . L’option de l’éditeur de liens **/Order** indique à l’éditeur de liens de placer les COMDAT dans l’image exécutable dans l’ordre que vous spécifiez.

Pour spécifier l’ordre COMDAT, créez un *fichier réponse*, un fichier texte qui répertorie chaque COMDAT par nom, une par ligne, dans l’ordre dans lequel vous souhaitez qu’elles soient placées par l’éditeur de liens. Transmettez le nom de ce fichier en tant que paramètre *filename* de l’option **/Order** . Pour les fonctions C++, le nom d’un COMDAT est la forme décorée du nom de la fonction. Utilisez le nom non décoré pour les fonctions C, `main` et pour les fonctions C++ déclarées comme `extern "C"` . Les noms de fonctions et les noms décorés respectent la casse. Pour plus d’informations sur les noms décorés, consultez [noms décorés](decorated-names.md).

Pour rechercher les noms décorés de vos COMDAT, utilisez l’option [/Symbols](symbols.md) de l’outil [DUMPBIN](dumpbin-reference.md) sur le fichier objet. L’éditeur de liens ajoute automatiquement un trait de soulignement ( **\_** ) à des noms de fonctions dans le fichier réponse, sauf si le nom commence par un point d’interrogation (**?**) ou au niveau du signe ( **\@** ). Par exemple, si un fichier source, example. cpp, contient des fonctions `int cpp_func(int)` , `extern "C" int c_func(int)` et `int main(void)` , la commande `DUMPBIN /SYMBOLS example.obj` répertorie ces noms décorés :

```Output
...
088 00000000 SECT1A notype ()    External     | ?cpp_func@@YAHH@Z (int __cdecl cpp_func(int))
089 00000000 SECT22 notype ()    External     | _c_func
08A 00000000 SECT24 notype ()    External     | _main
...
```

Dans ce cas, spécifiez les noms en tant que `?cpp_func@@YAHH@Z` , `c_func` et `main` dans votre fichier réponse.

Si plusieurs options **/Order** s’affichent dans les options de l’éditeur de liens, la dernière option spécifiée prend effet.

L’option **/Order** désactive les liens incrémentiels. Vous pouvez voir un avertissement de l’éditeur de liens [LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md) quand vous spécifiez cette option si l’édition de liens incrémentielle est activée, ou si vous avez spécifié l’option de compilateur [/ZI (incrémentiel PDB)](z7-zi-zi-debug-information-format.md) . Pour Silencer cet avertissement, vous pouvez utiliser l’option [/INCREMENTAL : no](incremental-link-incrementally.md) Linker pour désactiver l’édition de liens incrémentielle et utiliser l’option de compilateur [/ZI (Generate PDB)](z7-zi-zi-debug-information-format.md) pour générer un fichier PDB sans liaison incrémentielle.

> [!NOTE]
> LINK ne peut pas trier les fonctions statiques, car les noms de fonctions statiques ne sont pas des noms de symboles publics. Quand **/Order** est spécifié, l’avertissement de l’éditeur de liens [LNK4037](../../error-messages/tool-errors/linker-tools-warning-lnk4037.md) est généré pour chaque symbole dans le fichier de réponse de l’ordre qui est soit static, soit introuvable.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés optimisation de l’éditeur de liens **Propriétés de configuration**  >    >   .

1. Modifiez la propriété **ordre des fonctions** pour qu’elle contienne le nom de votre fichier réponse.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.FunctionOrder%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
