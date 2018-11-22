---
title: Ajouter une méthode
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.method.overview
- vc.codewiz.method.idlattrib
helpviewer_keywords:
- add method wizard [C++]
- methods [C++], adding
- methods [C++], adding using wizards
- IDL attributes, add method wizard
ms.assetid: 4ba4e45f-fa38-4d5e-af44-cbec0a7ab558
ms.openlocfilehash: 23fb05e633713016b1f6289f73a916502736af10
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51692683"
---
# <a name="add-a-method"></a>Ajouter une méthode

Vous pouvez utiliser l’[Assistant Ajout de méthode](#add-method-wizard) pour ajouter une méthode à une interface dans votre projet. Si le projet contient une classe associée à l’interface, l’Assistant modifie également la classe.

**Pour ajouter une méthode à votre objet**

1. Dans **Affichage de classes**, développez le nœud du projet pour afficher l’interface à laquelle vous souhaitez ajouter la méthode.

   > [!NOTE]
   > Vous pouvez également ajouter des méthodes aux dispinterfaces qui, tant que le projet n’est pas attribué, se trouvent sous le nœud de la bibliothèque.

1. Cliquez avec le bouton droit sur le nom de l’interface.

1. Dans le menu contextuel, choisissez **Ajouter**, puis **Ajouter une méthode**.

1. Dans l’Assistant Ajout de méthode, indiquez les informations permettant de créer la méthode.

1. Spécifiez tous les paramètres IDL (Interface Definition Language) pour cette méthode dans la page [Attributs IDL](#idl-attributes-add-method-wizard) de l’Assistant.

1. Sélectionnez **Terminer** pour ajouter la méthode.

## <a name="in-this-section"></a>Dans cette section

- [Assistant Ajout de méthode](#add-method-wizard)
- [Attributs IDL, Assistant Ajout de méthode](#idl-attributes-add-method-wizard)

## <a name="add-method-wizard"></a>Assistant Ajout de méthode

Utilisez cet Assistant pour ajouter une méthode à une interface. En fonction du type d’interface ou de projet auquel vous ajoutez une méthode, l’Assistant affiche différentes options.

### <a name="names"></a>Noms

- **Type de retour**

  Type de données retourné par la méthode. `HRESULT` est recommandé pour tous les types d’interface, car il fournit un moyen standard de retourner les erreurs.

  |Type d'interface|Description|
  |--------------------|-----------------|
  |Interface double|`HRESULT`. Non modifiable.|
  |Interface personnalisée|`HRESULT`. Non modifiable.|
  |Interface personnalisée locale|Fournissez votre propre type de retour ou sélectionnez-le dans la liste.|
  |Dispinterface|Fournissez votre propre type de retour ou sélectionnez-le dans la liste.|
  |Dispinterface du contrôle ActiveX MFC|Si vous implémentez une méthode stock, le type de retour est défini sur la valeur appropriée et n’est pas modifiable. Si vous sélectionnez une méthode dans la liste **Nom de la méthode** et sélectionnez **Personnalisé** sous **Sélectionner le type de méthode**, sélectionnez un type de retour dans la liste.|

- **Nom de la méthode**

  Définit le nom de la méthode.

  |Type d'interface|Description|
  |--------------------|-----------------|
  |Interface double ATL, interface personnalisée et interface personnalisée locale|Fournissez votre propre nom de méthode.|
  |Dispinterface MFC|Fournissez votre propre nom de méthode ou sélectionnez un nom de méthode dans la liste. Si vous sélectionnez un nom dans la liste, la valeur appropriée s’affiche dans la zone **Type de retour** et n’est pas modifiable.|
  |Dispinterface du contrôle ActiveX MFC|Fournissez la vôtre ou sélectionnez une des méthodes stock [DoClick](../mfc/reference/colecontrol-class.md#doclick) et [Refresh](../mfc/reference/colecontrol-class.md#refresh). Pour plus d’informations, consultez [Contrôles ActiveX MFC : Ajout de méthodes stock](../mfc/mfc-activex-controls-adding-stock-methods.md).|

- **Type de méthode**

  Disponible uniquement pour les contrôles ActiveX MFC. Si vous fournissez un nom de méthode dans la zone **Nom de la méthode** au lieu de sélectionner une méthode dans la liste, cette zone n’est pas disponible.

  Si vous sélectionnez une des méthodes de la liste **Nom de la méthode**, sélectionnez l’implémentation stock ou une implémentation personnalisée.

  |Type de méthode|Description|
  |-----------------|-----------------|
  |**Stock**|Valeur par défaut. Insère l’implémentation stock de la méthode que vous sélectionnez dans la liste **Nom de la méthode**. Le **Type de retour** n’est pas modifiable si vous sélectionnez **Stock**.|
  |**Personnalisé**|Insère une implémentation stub de la méthode sélectionnée dans la liste **Nom de la méthode**. Pour les types de méthodes personnalisées, vous pouvez fournir votre propre type de retour ou en sélectionner un dans la liste **Type de retour**.|

- **Nom interne**

  Disponible uniquement pour les méthodes personnalisées ajoutées à une dispinterface MFC. Définit le nom utilisé dans la table de dispatch, le fichier d’en-tête (.h) et le fichier d’implémentation (.cpp). Par défaut, ce nom est identique au **Nom de la méthode**. Vous pouvez changer le nom de la méthode si vous utilisez une dispinterface MFC ou que vous ajoutez une méthode personnalisée à une dispinterface du contrôle ActiveX MFC.

  |Type d'interface|Description|
  |--------------------|-----------------|
  |Interface double ATL, interface personnalisée et interface personnalisée locale|Non disponible.|
  |Dispinterface MFC|Définissez le nom de la méthode par défaut. Vous pouvez modifier le nom interne.|
  |Dispinterface du contrôle ActiveX MFC|Vous pouvez définir le nom interne uniquement pour les méthodes personnalisées. Les méthodes stock n’utilisent pas de nom interne.|

- **Attributs de paramètres**

  Définit des attributs supplémentaires pour le paramètre spécifié dans **Nom de paramètre**.

  |Attribut de paramètre|Description|Combinaisons autorisées|
  |-------------------------|-----------------|--------------------------|
  |**In**|Indique que le paramètre est transmis de la procédure appelante à la procédure appelée.|`in` uniquement<br /><br /> `in` et `out`|
  |**Out**|Indique que le paramètre de pointeur est retourné par la procédure appelée à la procédure appelante (du serveur au client).|`out` uniquement<br /><br /> `in` et `out`<br /><br /> `out` et `retval`|
  |**Retval**|Indique que le paramètre reçoit la valeur de retour du membre.|`retval` et `out`|

- **Type de paramètre**

  Définit le type de données du paramètre. Sélectionnez le type dans la liste.

- **Nom du paramètre**

  Définit le nom d’un paramètre à passer par l’intermédiaire de votre méthode. Après avoir tapé le nom, sélectionnez **Ajouter** pour l’ajouter à la liste de paramètres transmise par le biais de votre méthode. Si vous ne fournissez pas de nom de paramètre, l’Assistant ignore tous les attributs de paramètre (ATL uniquement) ou les sélections de **Type de paramètre**.

  Dès que vous sélectionnez **Ajouter**, le nom du paramètre s’affiche dans **Liste de paramètres**.

  > [!NOTE]
  > Si vous fournissez un nom de paramètre et sélectionnez **Terminer** avant de sélectionner **Ajouter**, le paramètre n’est pas ajouté à la méthode. Vous devez rechercher la méthode et insérer le paramètre manuellement.

- **Ajouter**

  Ajoute le paramètre que vous spécifiez dans **Nom du paramètre** ainsi que son type et les attributs de paramètre à **Liste de paramètres**. Sélectionnez **Ajouter** pour ajouter un paramètre à la liste.

- **Supprimer**

  Supprime de la liste le paramètre que vous sélectionnez dans **Liste de paramètres**.

- **Liste de paramètres**

  Affiche tous les paramètres ainsi que leurs modificateurs et types actuellement ajoutés pour la méthode. Quand vous ajoutez des paramètres, l’Assistant met à jour la **Liste de paramètres** pour afficher chaque paramètre avec son modificateur et son type.

## <a name="idl-attributes-add-method-wizard"></a>Attributs IDL, Assistant Ajout de méthode

Utilisez cette page de l’Assistant Ajout de méthode pour spécifier tous les paramètres IDL (Interface Definition Language) de la méthode.

- `id`

  Définit l’ID numérique qui identifie la méthode. Pour plus d’informations, consultez [id](/windows/desktop/Midl/id) dans les *Informations de référence MIDL*.

  Cette zone n’est pas disponible pour les interfaces personnalisées, ni pour les dispinterfaces MFC.

- `call_as`

  Spécifie le nom d’une méthode distante à laquelle cette méthode locale peut être mappée. Pour plus d’informations, consultez [call_as](/windows/desktop/Midl/call-as) dans les *Informations de référence MIDL*.

  Non disponible pour les dispinterfaces MFC.

- `helpcontext`

  Spécifie un ID de contexte qui permet à l'utilisateur de voir des informations sur cette méthode dans le fichier d’aide. Pour plus d’informations, consultez [helpcontext](/windows/desktop/Midl/helpcontext) dans les *Informations de référence MIDL*.

  Non disponible pour les dispinterfaces MFC.

- `helpstring`

  Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique. Par défaut, il s’agit de « method *nom_méthode* ». Pour plus d’informations, consultez [helpstring](/windows/desktop/Midl/helpstring) dans les *Informations de référence MIDL*.

  Non disponible pour les dispinterfaces MFC.

- **Attributs supplémentaires**

  Non disponible pour les dispinterfaces MFC.

  |Attribut|Description|
  |---------------|-----------------|
  |`hidden`|Indique que la méthode existe, mais qu’elle ne doit pas être affichée dans un navigateur orienté utilisateur. Pour plus d’informations, consultez [hidden](/windows/desktop/Midl/hidden) dans les *Informations de référence MIDL*.|
  |`source`|Indique qu’un membre de la méthode est une source d’événements. Pour plus d’informations, consultez [source](/windows/desktop/Midl/source) dans les *Informations de référence MIDL*.|
  |`local`|Indique au compilateur MIDL que la méthode n’est pas distante. Pour plus d’informations, consultez [local](/windows/desktop/Midl/local) dans les *Informations de référence MIDL*.|
  |`restricted`|Spécifie que la méthode ne peut pas être appelée arbitrairement. Pour plus d’informations, consultez [restricted](/windows/desktop/Midl/restricted) dans les *Informations de référence MIDL*.|
  |`vararg`|Spécifie que la méthode accepte un nombre variable d’arguments. Le dernier argument doit être un tableau sécurisé de type `VARIANT` qui contient le reste des arguments. Pour plus d’informations, consultez [vararg](/windows/desktop/Midl/vararg) dans les *Informations de référence MIDL*.|
