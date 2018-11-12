---
title: Noms, Assistant Ajout de propriété
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.prop.overview
ms.assetid: 0453b7ea-89cb-41a1-80a2-d45f61589c0a
ms.openlocfilehash: 1cb37b2e8f3efd9ff9789a315e6bf32add730708
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636915"
---
# <a name="names-add-property-wizard"></a>Noms, Assistant Ajout de propriété

Utilisez cet Assistant pour ajouter une propriété à une interface.

- **Type de propriété**

   Définit le type de propriété que vous ajoutez. Pour les dispinterfaces MFC, indiquez le type de votre choix ou sélectionnez-en un dans la liste prédéfinie. Si vous indiquez une implémentation stock d’une propriété, **Type de propriété** est défini sur le type de stock et n’est pas disponible à des fins de modification.

- **Nom de la propriété**

   Définit le nom de la propriété. Pour les dispinterfaces MFC associées aux contrôles ActiveX, vous pouvez indiquer le nom de votre choix ou sélectionner un nom de propriété stock dans la liste prédéfinie. Si vous indiquez votre propre nom de propriété, le type d’implémentation **Stock** n’est pas disponible. Pour obtenir une description des propriétés de la liste, consultez [Propriétés stock](../ide/stock-properties.md).

   |Type d'interface|Description|
   |--------------------|-----------------|
   |Interface double ATL, interface personnalisée et interface personnalisée locale|Indiquez un nom de propriété.|
   |Dispinterface MFC, dispinterface du contrôle ActiveX MFC|Indiquez un nom de propriété ou sélectionnez une propriété stock dans la liste. Si vous sélectionnez une propriété dans la liste, la valeur appropriée apparaît dans la zone **Type de propriété**. Vous pouvez modifier ce type selon la sélection que vous avez effectuée sous **Type d’implémentation**.|

- **Type de retour**

   Interfaces ATL uniquement. Définit le type de retour de la propriété. Pour les interfaces doubles, `HRESULT` est toujours le type de retour et cette zone n’est pas disponible. Pour les interfaces personnalisées, vous pouvez sélectionner un type de retour dans la liste. `HRESULT` est encore recommandé, parce qu’il offre un moyen standard de retourner des erreurs.

- **Nom de la variable**

   Dispinterfaces MFC uniquement. Disponible uniquement si vous spécifiez **Variable membre** sous **Type d’implémentation**. Définit le nom de la variable membre à laquelle la propriété est associée. Par défaut, le nom de la variable est défini sur m_*PropertyName*. Vous pouvez modifier ce nom.

- **Fonction de notification**

   Dispinterfaces MFC uniquement. Disponible uniquement si vous spécifiez **Variable membre** sous **Type d’implémentation**. Définit le nom de la fonction de notification appelée en cas de modification de la propriété. Par défaut, le nom de la fonction de notification est défini sur On*PropertyName*Changed. Vous pouvez modifier ce nom.

- **Get, fonction**

   Dispinterfaces MFC. Disponible uniquement si vous spécifiez **Méthodes Get/Set** sous **Type d’implémentation**. Définit le nom de la fonction pour obtenir la propriété. Par défaut, le nom de la fonction Get est défini sur Get*PropertyName*. Vous pouvez modifier ce nom. Si vous supprimez le nom, la fonction [GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported) est insérée dans la table de dispatch de l’interface. La fonction Get*PropertyName* spécifie que la propriété est accessible en lecture.

- **Fonction Set**

   Dispinterfaces MFC uniquement. Disponible uniquement si vous spécifiez **Méthodes Get/Set** sous **Type d’implémentation**. Définit le nom de la fonction pour définir la propriété. Par défaut, le nom de la fonction Set est défini sur Set*PropertyName*. Vous pouvez modifier ce nom. Si vous supprimez le nom, la fonction [SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported) est insérée dans la table de dispatch de l’interface. La fonction Set*PropertyName* spécifie que la propriété est accessible en écriture.

- **Type d’implémentation**

   Dispinterfaces MFC uniquement. Spécifie la méthode d’implémentation de la propriété ajoutée.

   |Type d’implémentation|Description|
   |-------------------------|-----------------|
   |**Stock**|Spécifie une implémentation stock pour la propriété sélectionnée dans **Nom de la propriété**. Valeur par défaut. Pour plus d’informations, consultez [Propriétés stock](../ide/stock-properties.md).<br /><br /> Si vous spécifiez **Stock**, puis **Type de propriété**, **Type de paramètre** et **Nom du paramètre** apparaissent estompés.|
   |**Variable membre**|Spécifie que la propriété est ajoutée comme variable membre. Vous pouvez ajouter des propriétés personnalisées ou la plupart des propriétés stock comme variables membres. Vous ne pouvez pas spécifier **Variable membre** pour les propriétés **Caption**, **hWnd** et **Text**.<br /><br /> Fournit les noms par défaut sous **Nom de la variable** et **Fonction de notification**. Vous pouvez modifier ce nom.|
   |**Méthodes Get/Set**|Spécifie que la propriété est ajoutée comme fonctions Get*PropertyName* et Set*PropertyName*, par défaut. Ces noms apparaissent sous **Get, fonction** et **Fonction Set**.<br /><br /> Vous pouvez modifier la valeur par défaut de **Type de propriété**, qui transmet une valeur pour la fonction Get. Vous pouvez spécifier des paramètres pour les fonctions **Get** et `Set`.|

- **Get, fonction**

   Interfaces ATL. Définit la propriété comme étant accessible en lecture ; en d’autres termes, cette fonction crée la méthode **Get** pour récupérer cette propriété de l’objet. Vous devez sélectionner **Get**, `Put`, ou les deux.

- **Fonction Put**

   Interfaces ATL uniquement. Définit la propriété comme étant accessible en écriture ; en d’autres termes, cette fonction crée la méthode `Put` pour définir cette propriété de l’objet. Vous devez sélectionner **Get**, `Put`, ou les deux. Si vous sélectionnez cette option, vous pouvez choisir l’une des deux méthodes décrites ci-après pour implémenter la méthode :

   |Option|Description|
   |------------|-----------------|
   |**PropPut**|La fonction [PropPut](../windows/propput.md) retourne une copie de l’objet. Cette option par défaut est la manière la plus courante de rendre la propriété accessible en écriture.|
   |**PropPutRef**|La fonction [PropPutRef](../windows/propputref.md) retourne une référence à l’objet et non la copie de l’objet lui-même. Utilisez de préférence cette option pour les objets, tels que les structures ou les tableaux volumineux, qui peuvent créer une charge de travail importante à l’initialisation.|

- **Attributs de paramètres**

   Interfaces ATL uniquement. Définit si le paramètre spécifié dans **Nom du paramètre** est **in**, **out**, les deux ou aucun.

   |Option|Description|
   |------------|-----------------|
   |**in**|Indique que le paramètre est transmis de la procédure appelante à la procédure appelée.|
   |**out**|Indique que le paramètre de pointeur est retourné par la procédure appelée à la procédure appelante (du serveur au client).|

- **Type de paramètre**

   Définit le type de données du paramètre. Sélectionnez le type dans la liste.

- **Nom du paramètre**

   Définit le nom d’un paramètre que vous ajoutez pour la propriété, si celle-ci comporte des paramètres. Une fois que vous cliquez sur **Ajouter**, le nom du paramètre s’affiche dans **Liste de paramètres**.

- **Liste de paramètres**

   Affiche la liste des attributs à ajouter à la propriété. Chaque élément de la liste comprend le nom du paramètre, le type du paramètre et les attributs. Utilisez **Ajouter** et **Supprimer** pour mettre à jour la liste.

- **Ajouter**

   Ajoute le paramètre spécifié dans les zones **Nom du paramètre** et **Type du paramètre** à la zone **Liste de paramètres**. Vous devez cliquer sur **Ajouter** pour ajouter un paramètre à la liste.

- **Supprimer**

   Supprime le paramètre que vous sélectionnez dans la zone **Liste de paramètres**.

- **Propriété par défaut**

   Dispinterface MFC uniquement. Définit cette propriété comme valeur par défaut pour l’interface. Une interface ne peut avoir qu’une propriété par défaut ; une fois la propriété par défaut spécifiée, cette zone n’est pas disponible pour toutes les autres propriétés que vous ajoutez à l’interface.

## <a name="see-also"></a>Voir aussi

[Ajout d’une propriété](../ide/adding-a-property-visual-cpp.md)<br>
[Attributs IDL, Assistant Ajout de propriété](../ide/idl-attributes-add-property-wizard.md)<br>
[Implémentation d’une interface](../ide/implementing-an-interface-visual-cpp.md)