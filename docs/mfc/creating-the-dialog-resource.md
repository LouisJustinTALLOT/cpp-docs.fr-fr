---
description: 'En savoir plus sur : création de la ressource de boîte de dialogue'
title: Création des ressources de boîte de dialogue
ms.date: 11/04/2016
helpviewer_keywords:
- dialog resources
- MFC dialog boxes [MFC], creating
- dialog templates [MFC], creating dialog resource
- templates [MFC], creating
- resources [MFC], creating dialog boxes
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 0b83bd33-14d3-4611-8129-fccdae18053e
ms.openlocfilehash: 999a63d11981b8d21be85096ff49813c92b15810
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309717"
---
# <a name="creating-the-dialog-resource"></a>Création des ressources de boîte de dialogue

Pour concevoir la [boîte de dialogue](dialog-boxes.md) et créer la ressource de boîte de dialogue, vous utilisez l' [éditeur de boîtes](../windows/dialog-editor.md)de dialogue. Dans l’éditeur de boîtes de dialogue, vous pouvez :

- Ajustez la taille et l’emplacement de votre boîte de dialogue lorsqu’elle s’affiche.

- Faites glisser différents genres de contrôles à partir d’une palette de contrôles et déposez-les là où vous le souhaitez dans la boîte de dialogue.

- Placez les contrôles à l’aide des boutons d’alignement sur la barre d’outils.

- Testez votre boîte de dialogue en simulant l’apparence et le comportement de votre programme. En mode test, vous pouvez manipuler les contrôles de la boîte de dialogue en tapant du texte dans les zones de texte, en cliquant sur les boutons de commande, et ainsi de suite.

Lorsque vous avez terminé, votre ressource de modèle de boîte de dialogue est stockée dans le fichier de script de ressources de votre application. Vous pouvez le modifier ultérieurement si nécessaire. Pour obtenir une description complète de la façon de créer et de modifier des ressources de boîte de dialogue, consultez les rubriques de l' [éditeur de boîtes de dialogue](../windows/dialog-editor.md) . Cette technique est également utilisée pour créer les ressources de modèle de boîte de dialogue pour les classes [CFormView](reference/cformview-class.md) et [CRecordView](reference/crecordview-class.md) .

Lorsque l’apparence de la boîte de dialogue vous convient, créez une classe de boîte de dialogue et mappez ses messages, comme décrit dans [création d’une classe de boîte de dialogue avec des assistants de code](creating-a-dialog-class-with-code-wizards.md).

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](dialog-boxes.md)<br/>
[Utilisation des boîtes de dialogue dans MFC](life-cycle-of-a-dialog-box.md)
