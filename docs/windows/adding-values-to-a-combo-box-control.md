---
title: Ajout de valeurs à un contrôle Combo Box | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.combo
dev_langs:
- C++
helpviewer_keywords:
- combo boxes [C++], Data property
- controls [C++], testing values in combo boxes
- combo boxes [C++], adding values
- combo boxes [C++], previewing values
- Data property
- combo boxes [C++], testing values
ms.assetid: 22a78f98-fada-48b3-90d8-7fa0d8e4de51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0812c05844bbff9d6a341ea5b5812c5e328c2d5b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373371"
---
# <a name="adding-values-to-a-combo-box-control"></a>Ajout de valeurs à un contrôle Combo Box

Vous pouvez ajouter des valeurs à un contrôle combo box tant que vous avez le **boîte de dialogue** éditeur ouvert.

> [!TIP]
> Il est judicieux d’ajouter toutes les valeurs à la zone de liste déroulante *avant* dimensionner la zone dans le **boîte de dialogue** éditeur ou texte qui doit apparaître dans le contrôle de liste déroulante peut être tronqué.

### <a name="to-enter-values-into-a-combo-box-control"></a>Pour entrer des valeurs dans un contrôle combo box

1. Sélectionnez le contrôle de zone de liste modifiable en cliquant dessus.

2. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), faites défiler jusqu'à la **données** propriété.

   > [!NOTE]
   > Si vous affichez les propriétés groupées par type, **données** s’affiche dans le **divers** propriétés.

3. Cliquez dans la zone de valeur pour le **données** propriété et tapez vos valeurs de données, séparées par des points-virgules.

   > [!NOTE]
   > Ne placez pas les espaces entre les valeurs car ils interfèrent avec le tri alphabétique dans la liste déroulante.

4. Cliquez sur **entrée** lorsque vous avez terminé d’ajouter des valeurs.

Pour plus d’informations sur l’agrandissement de la partie déroulante d’une zone de liste déroulante, consultez [définition de la taille de la zone de liste déroulante et de sa liste de déroulante](setting-the-size-of-the-combo-box-and-its-drop-down-list.md).

> [!NOTE]
> Vous ne pouvez pas ajouter des valeurs à des projets Win32 à l’aide de cette procédure (le **données** propriété apparaît en grisé pour les projets Win32). Car les projets Win32 n’ont pas de bibliothèques qui ajoutent cette fonctionnalité, vous devez ajouter par programmation des valeurs à une zone de liste déroulante avec un projet Win32.

### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>Pour tester l’apparence des valeurs dans une zone de liste déroulante

1. Après avoir entré les valeurs dans le **données** propriété, cliquez sur le **Test** bouton sur le [barre d’outils Éditeur de boîte de dialogue](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

   Faites défiler vers le bas la liste de valeur entière. Les valeurs s’affichent exactement comme ils sont tapés dans le **données** propriété dans le **propriétés** fenêtre. Il n’existe aucune orthographe ou la vérification de la mise en majuscules.

   Appuyez sur **ÉCHAP** pour revenir à la **boîte de dialogue** éditeur.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)<br/>
[Contrôles](../mfc/controls-mfc.md)