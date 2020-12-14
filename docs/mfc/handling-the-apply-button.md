---
description: 'En savoir plus sur : gestion du bouton appliquer'
title: Gestion du bouton Appliquer
ms.date: 11/04/2016
helpviewer_keywords:
- Apply button in property sheet
- property sheets, Apply button
ms.assetid: 7e977015-59b8-406f-b545-aad0bfd8d55b
ms.openlocfilehash: a626dcab04d68d19efba79465bfca46545ff6670
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254935"
---
# <a name="handling-the-apply-button"></a>Gestion du bouton Appliquer

Les feuilles de propriétés ont une fonction que les boîtes de dialogue standard n'ont pas : elles permettent à l'utilisateur d'appliquer les modifications qu'il a effectuées avant de fermer la feuille de propriétés. Cette opération s'effectue à l'aide du bouton Appliquer. Cet article décrit les méthodes que vous pouvez utiliser pour implémenter cette fonctionnalité correctement.

Les boîtes de dialogue modales sont généralement les paramètres d'un objet externe lorsque l'utilisateur clique sur OK pour fermer la boîte de dialogue. Il en va de même pour une feuille de propriétés : lorsque l'utilisateur clique sur OK, les nouveaux paramètres de la feuille de propriétés prennent effet.

Toutefois, vous pouvez permettre à l'utilisateur d'enregistrer des paramètres sans avoir à fermer la boîte de dialogue de la feuille de propriétés. Il s'agit de la fonction du bouton Appliquer. Le bouton Appliquer applique les paramètres dans toutes les pages de propriétés de l'objet externe, par opposition au fait d'appliquer uniquement les paramètres de la page actuellement active.

Par défaut, le bouton Appliquer reste désactivé. Vous devez écrire du code pour activer le bouton Appliquer aux moments appropriés, et vous devez écrire du code pour implémenter l'effet Appliquer, comme expliqué ci-dessous.

Si vous ne souhaitez pas proposer la fonctionnalité Appliquer à l'utilisateur, il n'est pas nécessaire de supprimer le bouton Appliquer. Vous pouvez la laisser désactiver, chose qui sera courante pour les applications qui utiliseront la prise en charge des feuilles de propriétés standard disponibles dans les prochaines versions de Windows.

Pour signaler qu’une page est modifiée et activer le bouton appliquer, appelez `CPropertyPage::SetModified( TRUE )` . Si l'une des pages fait état de modifications, le bouton Appliquer restera activé, indépendamment de si la page active a été modifiée ou pas.

Vous devez appeler [CPropertyPage :: SetModified](reference/cpropertypage-class.md#setmodified) chaque fois que l’utilisateur modifie des paramètres dans la page. Une façon de détecter quand un utilisateur modifie un paramètre dans la page consiste à implémenter des gestionnaires de notification de modification pour chacun des contrôles de la page de propriétés, par exemple **EN_CHANGE** ou **BN_CLICKED**.

Pour implémenter l'effet du bouton Appliquer, la feuille de propriétés doit indiquer son propriétaire, ou un autre objet externe dans l'application, pour appliquer les paramètres aux pages de propriétés. En même temps, la feuille de propriétés doit désactiver le bouton appliquer en appelant `CPropertyPage::SetModified( FALSE )` pour toutes les pages qui ont appliqué leurs modifications à l’objet externe.

Pour obtenir un exemple de ce processus, consultez l’exemple général MFC [PROPDLG](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Voir aussi

[Feuilles de propriétés](property-sheets-mfc.md)
