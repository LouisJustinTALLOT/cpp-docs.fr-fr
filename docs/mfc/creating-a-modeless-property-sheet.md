---
description: 'En savoir plus sur : création d’une feuille de propriétés non modale'
title: Création d'une feuille de propriétés non modale
ms.date: 11/04/2016
helpviewer_keywords:
- modeless property sheets
- property sheets, modeless
- Create method [MFC], property sheets
ms.assetid: eafd8a92-cc67-4a69-a5fb-742c920d1ae8
ms.openlocfilehash: 1eaec55fe3c7c69ba558a10616dc2658025282d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310055"
---
# <a name="creating-a-modeless-property-sheet"></a>Création d'une feuille de propriétés non modale

Généralement, les feuilles de propriétés que vous créez sont modales. Lorsque vous utilisez une feuille de propriétés modale, l'utilisateur doit la fermer avant d'utiliser une autre partie de l'application. Cet article décrit les méthodes que vous pouvez utiliser pour créer une feuille de propriétés non modale qui permet à l'utilisateur de la maintenir ouverte tout en utilisant d'autres parties de l'application.

Pour afficher une feuille de propriétés comme une boîte de dialogue non modale et non comme une boîte de dialogue modale, appelez [CPropertySheet :: Create](reference/cpropertysheet-class.md#create) au lieu de [DoModal.](reference/cpropertysheet-class.md#domodal) Vous devez également implémenter des tâches supplémentaires pour prendre en charge une feuille de propriétés non modale.

L’une des tâches supplémentaires consiste à échanger des données entre la feuille de propriétés et l’objet externe qu’elle modifie lorsqu’elle est ouverte. Il s'agit généralement de la même tâche que pour les boîtes de dialogue non modales standard. Une partie de cette tâche implémente un canal de communication entre la feuille de propriétés non modale et l’objet externe auquel les paramètres de propriété s’appliquent. Cette implémentation est beaucoup plus facile si vous dérivez une classe de [CPropertySheet](reference/cpropertysheet-class.md) pour votre feuille de propriétés non modale. Cet article suppose que vous l'avez fait.

Une méthode pour communiquer entre la feuille de propriétés non modale et l'objet externe (la sélection actuelle dans une vue, par exemple) consiste à définir un pointeur de la feuille de propriétés vers l'objet externe. Définissez une fonction (appelée `SetMyExternalObject`, par exemple) dans la classe dérivée de `CPropertySheet` pour modifier le pointeur chaque fois que le focus passe d'un objet externe à un autre. La fonction `SetMyExternalObject` doit réinitialiser les paramètres de chaque page de propriétés pour refléter l'objet externe que vous venez de sélectionner. Pour ce faire, la `SetMyExternalObject` fonction doit être en mesure d’accéder aux objets [CPropertyPage](reference/cpropertypage-class.md) appartenant à la `CPropertySheet` classe.

La méthode la plus pratique pour fournir un accès aux pages de propriétés d'une feuille de propriétés consiste à incorporer les objets `CPropertyPage` dans l'objet dérivé de `CPropertySheet`. L’incorporation d' `CPropertyPage` objets dans l' `CPropertySheet` objet dérivé de diffère de la conception classique pour les boîtes de dialogue modales, où le propriétaire de la feuille de propriétés crée les `CPropertyPage` objets et les passe à la feuille de propriétés via [CPropertySheet :: AddPage](reference/cpropertysheet-class.md#addpage).

Il existe de nombreuses solutions dans l'interface utilisateur pour déterminer quand les paramètres de la feuille de propriétés non modale doivent être appliqués à un objet externe. Une solution consiste à appliquer les paramètres de la page de propriétés active lorsque l'utilisateur modifie une valeur. Une autre solution consiste à fournir un bouton Appliquer, qui permet à l’utilisateur d’accumuler les modifications des pages de propriétés avant de les valider dans l’objet externe. Pour plus d’informations sur les façons de gérer le bouton appliquer, consultez l’article [gestion du bouton appliquer](handling-the-apply-button.md).

## <a name="see-also"></a>Voir aussi

[Feuilles de propriétés](property-sheets-mfc.md)<br/>
[Échange de données](exchanging-data.md)<br/>
[Utilisation des boîtes de dialogue dans MFC](life-cycle-of-a-dialog-box.md)
