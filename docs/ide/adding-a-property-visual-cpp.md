---
title: Ajouter une propriété
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.prop.overview
- vc.codewiz.prop.idlattributes
helpviewer_keywords:
- interfaces, adding properties
- properties [C++], adding to interfaces
- names, add property wizard
- IDL attributes, add property wizard
- stock properties, about stock properties
- stock properties
ms.assetid: 37bd4db7-efd3-4faa-87ad-64902ed16a36
ms.openlocfilehash: 06940bb72f9113e0a8148e15418504b35fc95099
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694255"
---
# <a name="add-a-property"></a>Ajouter une propriété

Vous pouvez utiliser l’[Assistant Ajout de propriété](#names-add-property-wizard) pour ajouter une propriété à une interface de votre projet.

**Pour ajouter une propriété à votre objet**

1. Dans [l’affichage de classes](/visualstudio/ide/viewing-the-structure-of-code), cliquez avec le bouton droit sur le nom de l’interface à laquelle vous souhaitez ajouter la propriété.

   > [!NOTE]
   > Vous pouvez également ajouter des propriétés aux dispinterfaces qui, tant que le projet n’est pas attribué, sont imbriquées dans le nœud de la bibliothèque.

1. Dans le menu contextuel, choisissez **Ajouter**, puis **Ajouter une propriété**.

1. Dans l’[Assistant Ajout de propriété](#names-add-property-wizard), indiquez les informations permettant de créer la propriété.

1. Spécifiez tous les paramètres IDL (Interface Definition Language) pour la propriété dans la page [Attributs IDL](#idl-attributes-add-property-wizard) de l’Assistant.

1. Sélectionnez **Terminer** pour ajouter la propriété.

Les méthodes `Get` et `Put` de la propriété sont affichées sous la forme de deux icônes dans Affichage de classes, sous l’interface où elle est définie. Vous pouvez double-cliquer sur l’une ou l’autre des icônes pour voir la déclaration de propriété dans le fichier .idl.

- Pour les interfaces ATL, les fonctions `Get` et `Put` sont ajoutées au fichier .cpp, et les références à ces fonctions sont ajoutées au fichier .h.

- Pour les dispinterfaces MFC, si vous sélectionnez **Variable membre** comme type d’implémentation, une méthode et une variable sont ajoutées à la classe qui l’implémente. Si vous sélectionnez **Méthodes Get/Set** comme type d’implémentation, deux méthodes sont ajoutées à la classe qui l’implémente.

## <a name="in-this-section"></a>Dans cette section

- [Noms, Assistant Ajout de propriété](#names-add-property-wizard)
- [Attributs IDL, Assistant Ajout de propriété](#idl-attributes-add-property-wizard)
- [Propriétés stock](#stock-properties)

## <a name="names-add-property-wizard"></a>Noms, Assistant Ajout de propriété

Utilisez cet Assistant pour ajouter une propriété à une interface.

- **Type de propriété**

  Définit le type de propriété que vous ajoutez. Pour les dispinterfaces MFC, indiquez le type de votre choix ou sélectionnez-en un dans la liste prédéfinie. Si vous indiquez une implémentation stock d’une propriété, **Type de propriété** est défini sur le type de stock et n’est pas disponible à des fins de modification.

- **Nom de la propriété**

  Définit le nom de la propriété. Pour les dispinterfaces MFC associées aux contrôles ActiveX, vous pouvez indiquer le nom de votre choix ou sélectionner un nom de propriété stock dans la liste prédéfinie. Si vous indiquez votre propre nom de propriété, le type d’implémentation **Stock** n’est pas disponible. Pour obtenir une description des propriétés de la liste, consultez [Propriétés stock](#stock-properties).

  |Type d'interface|Description|
  |--------------------|-----------------|
  |Interface double ATL, interface personnalisée et interface personnalisée locale|Indiquez un nom de propriété.|
  |Dispinterface MFC, dispinterface du contrôle ActiveX MFC|Indiquez un nom de propriété ou sélectionnez une propriété stock dans la liste. Si vous sélectionnez une propriété dans la liste, la valeur appropriée apparaît dans la zone **Type de propriété**. Vous pouvez modifier ce type selon la sélection que vous avez effectuée sous **Type d’implémentation**.|

- **Type de retour**

  Interfaces ATL uniquement. Définit le type de retour de la propriété. Pour les interfaces doubles, `HRESULT` est toujours le type de retour et cette zone n’est pas disponible. Pour les interfaces personnalisées, vous pouvez sélectionner un type de retour dans la liste. `HRESULT` est encore recommandé, parce qu’il offre un moyen standard de retourner des erreurs.

- **Nom de la variable**

  Dispinterfaces MFC uniquement. Disponible uniquement si vous spécifiez **Variable membre** sous **Type d’implémentation**. Définit le nom de la variable membre à laquelle la propriété est associée. Par défaut, le nom de la variable est `m_`*PropertyName*. Vous pouvez modifier ce nom.

- **Fonction de notification**

  Dispinterfaces MFC uniquement. Disponible uniquement si vous spécifiez **Variable membre** sous **Type d’implémentation**. Définit le nom de la fonction de notification appelée en cas de modification de la propriété. Par défaut, le nom de la fonction de notification est `On`*PropertyName*`Changed`. Vous pouvez modifier ce nom.

- **Get, fonction**

  Dispinterfaces MFC. Disponible uniquement si vous spécifiez **Méthodes Get/Set** sous **Type d’implémentation**. Définit le nom de la fonction pour obtenir la propriété. Par défaut, le nom de la fonction `Get` est `Get`*PropertyName*. Vous pouvez modifier ce nom. Si vous supprimez le nom, la fonction [GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported) est insérée dans la table de dispatch de l’interface. La fonction `Get`*PropertyName* spécifie que la propriété est accessible en lecture.

- **Fonction Set**

  Dispinterfaces MFC uniquement. Disponible uniquement si vous spécifiez **Méthodes Get/Set** sous **Type d’implémentation**. Définit le nom de la fonction pour définir la propriété. Par défaut, le nom de la fonction `Set` est `Set`*PropertyName*. Vous pouvez modifier ce nom. Si vous supprimez le nom, la fonction [SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported) est insérée dans la table de dispatch de l’interface. La fonction `Set`*PropertyName* spécifie que la propriété est accessible en écriture.

- **Type d’implémentation**

  Dispinterfaces MFC uniquement. Spécifie comment implémenter la propriété ajoutée.

  |Type d’implémentation|Description|
  |-------------------------|-----------------|
  |**Stock**|Spécifie une implémentation stock pour la propriété sélectionnée dans **Nom de la propriété**. Valeur par défaut. Pour plus d’informations, consultez [Propriétés stock](#stock-properties).<br /><br /> Si vous spécifiez **Stock**, puis **Type de propriété**, **Type de paramètre** et **Nom du paramètre** apparaissent estompés.|
  |**Variable membre**|Spécifie que la propriété est ajoutée comme variable membre. Vous pouvez ajouter des propriétés personnalisées ou la plupart des propriétés stock comme variables membres. Vous ne pouvez pas spécifier **Variable membre** pour les propriétés `Caption`, `hWnd` et `Text`.<br /><br /> Fournit les noms par défaut sous **Nom de la variable** et **Fonction de notification**. Vous pouvez modifier ce nom.|
  |**Méthodes Get/Set**|Spécifie que la propriété est ajoutée comme fonctions `Get`*PropertyName* et `Set`*PropertyName*, par défaut. Ces noms apparaissent sous **Get, fonction** et **Fonction Set**.<br /><br /> Vous pouvez modifier la valeur par défaut de **Type de propriété**, qui transmet une valeur pour la fonction Get. Vous pouvez spécifier des paramètres pour les fonctions `Get` et `Set`.|

- **Get, fonction**

  Interfaces ATL. Définit la propriété comme étant accessible en lecture ; en d’autres termes, cette fonction crée la méthode `Get` pour récupérer cette propriété de l’objet. Sélectionnez **Get**, **Put** ou les deux.

- **Fonction Put**

  Interfaces ATL uniquement. Définit la propriété comme étant accessible en écriture ; en d’autres termes, cette fonction crée la méthode `Put` pour définir cette propriété de l’objet. Sélectionnez **Get**, **Put** ou les deux. Si vous sélectionnez cette option, vous pouvez choisir l’une des deux méthodes décrites ci-après pour implémenter la méthode :

  |Option|Description|
  |------------|-----------------|
  |**PropPut**|La fonction [PropPut](../windows/propput.md) retourne une copie de l’objet. Cette option par défaut est la manière la plus courante de rendre la propriété accessible en écriture.|
  |**PropPutRef**|La fonction [PropPutRef](../windows/propputref.md) retourne une référence à l’objet et non la copie de l’objet lui-même. Utilisez de préférence cette option pour les objets, tels que les structures ou les tableaux volumineux, qui peuvent créer une charge de travail importante à l’initialisation.|

- **Attributs de paramètres**

  Interfaces ATL uniquement. Définit si le paramètre spécifié dans **Nom du paramètre** est `in`, `out`, les deux ou aucun des deux.

  |Option|Description|
  |------------|-----------------|
  |`in`|Indique que le paramètre est transmis de la procédure appelante à la procédure appelée.|
  |`out`|Indique que le paramètre de pointeur est retourné par la procédure appelée à la procédure appelante (du serveur au client).|

- **Type de paramètre**

  Définit le type de données du paramètre. Sélectionnez le type dans la liste.

- **Nom du paramètre**

  Définit le nom d’un paramètre que vous ajoutez pour la propriété, si celle-ci comporte des paramètres. Dès que vous sélectionnez **Ajouter**, le nom du paramètre s’affiche dans **Liste de paramètres**.

- **Liste de paramètres**

  Affiche la liste des attributs à ajouter à la propriété. Chaque élément de la liste comprend le nom du paramètre, le type du paramètre et les attributs. Utilisez **Ajouter** et **Supprimer** pour mettre à jour la liste.

- **Ajouter**

  Ajoute le paramètre spécifié dans les zones **Nom du paramètre** et **Type du paramètre** à la zone **Liste de paramètres**. Sélectionnez **Ajouter** pour ajouter un paramètre à la liste.

- **Supprimer**

  Supprime le paramètre que vous sélectionnez dans la zone **Liste de paramètres**.

- **Propriété par défaut**

  Dispinterface MFC uniquement. Définit cette propriété comme valeur par défaut pour l’interface. Une interface ne peut avoir qu’une propriété par défaut ; une fois la propriété par défaut spécifiée, cette zone n’est pas disponible pour toutes les autres propriétés que vous ajoutez à l’interface.

## <a name="idl-attributes-add-property-wizard"></a>Attributs IDL, Assistant Ajout de propriété

Utilisez cette page de l’Assistant Ajout de propriété pour spécifier tous les paramètres IDL (Interface Definition Language) de la propriété.

- `id`

  Définit l’ID numérique qui identifie la propriété. Cette option n’est pas disponible pour les propriétés des interfaces personnalisées. Consultez [id](/windows/desktop/Midl/id) dans les *Informations de référence MIDL*.

- `helpcontext`

  Spécifie un ID de contexte qui permet à l’utilisateur de voir des informations sur cette propriété dans le fichier d’aide. Consultez [helpcontext](/windows/desktop/Midl/helpcontext) dans les *Informations de référence MIDL*.

- `helpstring`

  Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique. Par défaut, sa valeur est `property`&nbsp;*nom_propriété*. Consultez [helpstring](/windows/desktop/Midl/helpstring) dans les *Informations de référence MIDL*.

### <a name="other-options"></a>Autres options

Les options ne sont pas toutes disponibles pour tous les types de propriété.

|Option|Description|
|------------|-----------------|
|`bindable`|Indique que la propriété prend en charge la liaison de données. Consultez [bindable](/windows/desktop/Midl/bindable) dans les *Informations de référence MIDL*. Pour l’implémentation stock de la propriété, cette option est définie par défaut et n’est pas modifiable.|
|`defaultbind`|Indique que cette seule propriété prenant en charge la liaison de données représente le mieux l’objet. Consultez [defaultbind](/windows/desktop/Midl/defaultbind) dans les *Informations de référence MIDL*.|
|`displaybind`|Indique que cette propriété doit être montrée à l’utilisateur comme pouvant être liée. Consultez [displaybind](/windows/desktop/Midl/displaybind) dans les *Informations de référence MIDL*.|
|`immediatebind`|Indique que la base de données est immédiatement avertie de tout changement de cette propriété d’un objet lié aux données. Consultez [immediatebind](/windows/desktop/Midl/immediatebind) dans les *Informations de référence MIDL*.|
|`defaultcollelem`|Indique que la propriété est une fonction d’accesseur pour un élément de la collection par défaut. Consultez [defaultcollelem](/windows/desktop/Midl/defaultcollelem) dans les *Informations de référence MIDL*.|
|`nonbrowsable`|Marque un membre d’interface ou de dispinterface qui ne doit pas être affiché dans un navigateur de propriétés. Consultez [nonbrowsable](/windows/desktop/Midl/nonbrowsable) dans les *Informations de référence MIDL*.|
|`requestedit`|Indique que la propriété prend en charge la notification `OnRequestEdit`. Consultez [requestedit](/windows/desktop/Midl/requestedit) dans les *Informations de référence MIDL*. Pour l’implémentation stock de la propriété, cette option est définie par défaut et n’est pas modifiable.|
|`source`|Indique qu’un membre de la propriété est une source d’événements. Consultez [source](/windows/desktop/Midl/source) dans les *Informations de référence MIDL*.|
|`hidden`|Indique que la propriété existe, mais qu’elle ne doit pas être affichée dans un navigateur orienté utilisateur. Consultez [hidden](/windows/desktop/Midl/hidden) dans les *Informations de référence MIDL*.|
|`restricted`|Spécifie que la propriété ne peut pas être appelée arbitrairement. Consultez [restricted](/windows/desktop/Midl/restricted) dans les *Informations de référence MIDL*.|
|`local`|Indique au compilateur MIDL que la propriété n’est pas distante. Consultez [local](/windows/desktop/Midl/local) dans les *Informations de référence MIDL*.|

## <a name="stock-properties"></a>Propriétés stock

Si vous ajoutez une propriété à une dispinterface MFC à l’aide de l’[Assistant Ajout de propriété](#idl-attributes-add-property-wizard), vous pouvez choisir une propriété stock dans la liste **Nom de la propriété** de la page [Noms](../ide/names-add-property-wizard.md) de l’Assistant. Ces propriétés sont les suivantes :

|Nom de propriété|Description|
|-------------------|-----------------|
|`Appearance`|Retourne ou définit une valeur qui détermine l’apparence du contrôle. La propriété `Appearance` du contrôle peut inclure ou omettre les effets 3D. Il s’agit d’une propriété ambiante en lecture/écriture.|
|`BackColor`|Retourne ou définit la propriété `BackColor` ambiante du contrôle avec une couleur de palette (RVB) ou une couleur système prédéfinie. Par défaut, sa valeur correspond à la couleur de premier plan du conteneur du contrôle. Il s’agit d’une propriété ambiante en lecture/écriture.|
|`BorderStyle`|Retourne ou définit le style de bordure d’un contrôle. Il s’agit d’une propriété en lecture/écriture.|
|`Caption`|Retourne ou définit la propriété `Caption` du contrôle. La légende est le titre de la fenêtre. `Caption` n’a pas de type d’implémentation **Variable membre**.|
|`Enabled`|Retourne ou définit la propriété `Enabled` du contrôle. Un contrôle activé peut répondre aux événements générés par l’utilisateur.|
|`Font`|Retourne ou définit la police ambiante du contrôle. Null si le contrôle n’a pas de police.|
|`ForeColor`|Retourne ou définit la propriété `ForeColor` ambiante du contrôle.|
|`hWnd`|Retourne ou définit la propriété `hWnd` du contrôle. `hWnd` n’a pas de type d’implémentation **Variable membre**.|
|`ReadyState`|Retourne ou définit la propriété `ReadyState` du contrôle. Un contrôle peut être non initialisé, initialisé, en cours de chargement, interactif ou complet. Pour plus d’informations, consultez [READYSTATE](https://msdn.microsoft.com/library/aa768362.aspx) dans le *kit SDK Internet*.|
|`Text`|Retourne ou définit le texte présent dans un contrôle. `Text` n’a pas de type d’implémentation **Variable membre**.|
