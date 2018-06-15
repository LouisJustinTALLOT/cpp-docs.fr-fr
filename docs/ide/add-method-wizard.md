---
title: Assistant Ajout de méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.method.overview
dev_langs:
- C++
helpviewer_keywords:
- Add Method Wizard [C++]
- methods [C++], adding using wizards
ms.assetid: b9a71b0e-9ecf-40fa-9f86-4200cb23d671
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cc2ebd18640f0ab778cb45252691e63206861d53
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33340344"
---
# <a name="add-method-wizard"></a>Assistant Ajout de méthode
Utilisez cet Assistant pour ajouter une méthode à une interface. Selon le type d’interface ou de projet auquel vous ajoutez une méthode, l’Assistant affiche différentes options.  
  
## <a name="names"></a>Noms  
 **Type de retour**  
 Type de données retourné par la méthode. `HRESULT` est recommandé pour tous les types d’interface, car il fournit un moyen standard de retourner les erreurs.  
  
|Type d'interface|Description|  
|--------------------|-----------------|  
|Interface double|`HRESULT`. Non modifiable.|  
|Interface personnalisée|`HRESULT`. Non modifiable.|  
|Interface personnalisée locale|Fournissez votre propre type de retour ou sélectionnez-le dans la liste.|  
|Dispinterface|Fournissez votre propre type de retour ou sélectionnez-le dans la liste.|  
|Dispinterface du contrôle ActiveX MFC|Si vous implémentez une méthode stock, le type de retour est défini sur la valeur appropriée et n’est pas modifiable. Si vous sélectionnez une méthode dans la liste **Nom de la méthode** et cliquez sur **Personnalisé** sous **Sélectionner le type de méthode**, sélectionnez un type de retour dans la liste.|  
  
 **Nom de la méthode**  
 Définit le nom de la méthode.  
  
|Type d'interface|Description|  
|--------------------|-----------------|  
|Interface double ATL, interface personnalisée et interface personnalisée locale|Fournissez votre propre nom de méthode.|  
|Dispinterface MFC|Fournissez votre propre nom de méthode ou sélectionnez un nom de méthode dans la liste. Si vous sélectionnez un nom dans la liste, la valeur appropriée s’affiche dans la zone **Type de retour** et n’est pas modifiable.|  
|Dispinterface du contrôle ActiveX MFC|Fournissez la vôtre ou sélectionnez une des méthodes stock [DoClick](../mfc/reference/colecontrol-class.md#doclick) et [Refresh](../mfc/reference/colecontrol-class.md#refresh). Consultez [Contrôles ActiveX MFC : Ajout de méthodes stock](../mfc/mfc-activex-controls-adding-stock-methods.md) pour plus d’informations.|  
  
 **Type de méthode**  
 Disponible uniquement pour les contrôles ActiveX MFC. Si vous fournissez un nom de méthode dans la zone **Nom de la méthode** au lieu de sélectionner une méthode dans la liste, cette zone n’est pas disponible.  
  
 Si vous sélectionnez une des méthodes de la liste **Nom de la méthode**, sélectionnez l’implémentation stock ou une implémentation personnalisée.  
  
|Type de méthode|Description|  
|-----------------|-----------------|  
|**Stock**|Valeur par défaut. Insère l’implémentation stock de la méthode que vous sélectionnez dans la liste **Nom de la méthode**. Le **Type de retour** n’est pas modifiable si vous sélectionnez **Stock**.|  
|**Personnalisé**|Insère une implémentation stub de la méthode sélectionnée dans la liste **Nom de la méthode**. Pour les types de méthodes personnalisées, vous pouvez fournir votre propre type de retour ou en sélectionner un dans la liste **Type de retour**.|  
  
 **Nom interne**  
 Disponible uniquement pour les méthodes personnalisées ajoutées à une dispinterface MFC. Définit le nom utilisé dans la table de dispatch, le fichier d’en-tête (.h) et le fichier d’implémentation (.cpp). Par défaut, ce nom est identique au **Nom de la méthode**. Vous pouvez changer le nom de la méthode si vous utilisez une dispinterface MFC ou que vous ajoutez une méthode personnalisée à une dispinterface du contrôle ActiveX MFC.  
  
|Type d'interface|Description|  
|--------------------|-----------------|  
|Interface double ATL, interface personnalisée et interface personnalisée locale|Non disponible|  
|Dispinterface MFC|Définissez le nom de la méthode par défaut. Vous pouvez modifier le nom interne.|  
|Dispinterface du contrôle ActiveX MFC|Vous pouvez définir le nom interne uniquement pour les méthodes personnalisées. Les méthodes stock n’utilisent pas de nom interne.|  
  
 **Attributs de paramètre**  
 Définit des attributs supplémentaires pour le paramètre spécifié dans **Nom de paramètre**.  
  
|Attribut de paramètre|Description|Combinaisons autorisées|  
|-------------------------|-----------------|--------------------------|  
|**In**|Indique que le paramètre est transmis de la procédure appelante à la procédure appelée.|**in** uniquement<br /><br /> **in** et **out**|  
|**Out**|Indique que le paramètre de pointeur est retourné par la procédure appelée à la procédure appelante (du serveur au client).|**out** uniquement<br /><br /> **in** et **out**<br /><br /> **out** et **retval**|  
|**Retval**|Indique que le paramètre reçoit la valeur de retour du membre.|**retval** et out|  
  
 **Type de paramètre**  
 Définit le type de données du paramètre. Sélectionnez le type dans la liste.  
  
 **Nom du paramètre**  
 Définit le nom d’un paramètre à passer par l’intermédiaire de votre méthode. Après avoir tapé le nom, vous devez cliquer sur **Ajouter** pour l’ajouter à la liste de paramètres transmise par le biais de votre méthode. Si vous ne fournissez pas de nom de paramètre, l’Assistant ignore tous les attributs de paramètre (ATL uniquement) ou les sélections de **Type de paramètre**.  
  
 Dès que vous cliquez sur **Ajouter**, le nom du paramètre s’affiche dans **Liste de paramètres**.  
  
 **Remarque** Si vous fournissez un nom de paramètre, puis cliquez sur **Terminer** avant de cliquer sur **Ajouter**, le paramètre n’est pas ajouté à la méthode. Vous devez rechercher la méthode et insérer le paramètre manuellement.  
  
 **Ajouter**  
 Ajoute le paramètre que vous spécifiez dans **Nom du paramètre** ainsi que son type et les attributs de paramètre à **Liste de paramètres**. Vous devez cliquer sur **Ajouter** pour ajouter un paramètre à la liste.  
  
 **Supprimer**  
 Supprime de la liste le paramètre que vous sélectionnez dans **Liste de paramètres**.  
  
 **Liste de paramètres**  
 Affiche tous les paramètres ainsi que leurs modificateurs et types actuellement ajoutés pour la méthode. Quand vous ajoutez des paramètres, l’Assistant met à jour la **Liste de paramètres** pour afficher chaque paramètre avec son modificateur et son type.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout d’une méthode](../ide/adding-a-method-visual-cpp.md)   
 [Attributs IDL, Assistant Ajout de méthode](../ide/idl-attributes-add-method-wizard.md)