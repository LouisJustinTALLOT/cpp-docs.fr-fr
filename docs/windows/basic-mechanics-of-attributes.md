---
title: Mécanismes de base des attributs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], inserting in code
- attributes [C++/CLI], about attributes
ms.assetid: dc2069c3-b9f3-4a72-965c-4e5208ce8e34
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6f6563d61988beb5df91ce0a3ccb871e3a5a9adc
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315942"
---
# <a name="basic-mechanics-of-attributes"></a>Mécanismes de base des attributs

Il existe trois façons d’insérer des attributs dans votre projet. Tout d’abord, vous pouvez les insérer manuellement dans votre code source. Ensuite, vous pouvez insérer à l’aide de la grille des propriétés d’un objet dans votre projet. Enfin, vous pouvez insérer à l’aide de différents Assistants. Pour plus d’informations sur l’utilisation de la **propriétés** fenêtre et les différents Assistants, consultez [création et gestion de projets Visual C++](../ide/creating-and-managing-visual-cpp-projects.md).

Comme précédemment, lorsque le projet est généré, le compilateur analyse chaque fichier source C++, produit un fichier objet. Toutefois, lorsque le compilateur rencontre un attribut, il est analysé et sa syntaxe est vérifiée. Le compilateur appelle ensuite dynamiquement un fournisseur d’attributs pour insérer du code ou apporter d’autres modifications à la compilation. L’implémentation du fournisseur diffère selon le type d’attribut. Par exemple, les attributs liés à ATL sont implémentés par Atlprov.dll.

La figure suivante montre la relation entre le compilateur et le fournisseur d’attributs.

![Communication des attributs de composant](../windows/media/vccompattrcomm.gif "vcCompAttrComm")

> [!NOTE]
> L’utilisation d’attribut ne modifie pas le contenu du fichier source. Le seul moment où que le code généré d’attribut est visible est au cours de sessions de débogage. En outre, pour chaque fichier source dans le projet, vous pouvez générer un fichier texte qui affiche les résultats de la substitution de l’attribut. Pour plus d’informations sur cette procédure, consultez [/Fx (fusionner le Code injecté)](../build/reference/fx-merge-injected-code.md) et [débogage de Code injecté](/visualstudio/debugger/how-to-debug-injected-code).

Comme la plupart des constructions C++, les attributs ont un ensemble de caractéristiques qui définit leur utilisation appropriée. Cela est appelé le contexte de l’attribut et est traité dans la table de contexte d’attribut pour chaque rubrique de référence d’attribut. Par exemple, le [coclasse](../windows/coclass.md) attribut peut uniquement être appliqué à une classe existante ou une structure, par opposition à la [cpp_quote](../windows/cpp-quote.md) attribut, qui peut être inséré n’importe où dans un fichier source C++.

## <a name="see-also"></a>Voir aussi

[Concepts](../windows/attributed-programming-concepts.md)