---
title: Affectation des touches d’accès rapide aux commandes de Menu (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- access keys [C++], checking
- menus [C++], shortcut keys
- keyboard shortcuts [C++], command assignments
- access keys [C++], assigning
- mnemonics [C++], adding to menus
- keyboard shortcuts [C++], uniqueness checking
- mnemonics [C++], uniqueness checking
- Check Mnemonics command
ms.assetid: fbcf1a00-af6a-4171-805a-0ac01d4e8b0d
ms.openlocfilehash: 7a3302f7744bf5c3a0cbaac96de04d9f649fac10
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587328"
---
# <a name="assigning-access-keys-to-menu-commands-c"></a>Affectation des touches d’accès rapide aux commandes de Menu (C++)

Dans un projet C++, vous pouvez affecter une clé d’accès (un mnémonique qui permet à l’utilisateur de sélectionner le menu à l’aide du clavier) à vos menus et les commandes de menu.

### <a name="to-assign-an-access-shortcut-key-to-a-menu-command"></a>Pour affecter une touche d’accès (raccourci) à une commande de menu

1. Tapez une esperluette (`&`) devant une lettre dans le nom de menu ou le nom de commande pour spécifier cette lettre comme touche d’accès correspondant. Par exemple « & fichier » définit **Alt**+**F** comme touche de raccourci pour le **fichier** menu dans les applications écrites pour Microsoft Windows.

   L’élément de menu fournit un indice visuel signalant qu’une touche de raccourci est affectée à l’une de lettres. La lettre qui suit que le symbole & apparaît soulignée (en fonction du système d’exploitation).

   > [!NOTE]
   > Assurez-vous que toutes les touches d’accès rapide d’un menu sont uniques en cliquant avec le bouton droit sur le menu et en choisissant **Vérifier les mnémoniques** dans le menu contextuel.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur de menus](../windows/menu-editor.md)