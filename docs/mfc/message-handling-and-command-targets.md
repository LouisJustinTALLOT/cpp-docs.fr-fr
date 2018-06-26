---
title: Message de traitement et cibles des commandes | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- IOleCommandTarget
dev_langs:
- C++
helpviewer_keywords:
- command targets [MFC]
- message handling [MFC], active documents
- IOleCommandTarget interface [MFC]
- command routing [MFC], command targets
ms.assetid: e45ce14c-e6b6-4262-8f3b-4e891e0ec2a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc0f00e4f660036e73e96d4beb999d37453bdf26
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929354"
---
# <a name="message-handling-and-command-targets"></a>Gestion des messages et cibles des commandes
L'interface de dispatch de commande `IOleCommandTarget` définit un mécanisme simple et extensible pour interroger et exécuter des commandes. Ce mécanisme est plus simple qu'`IDispatch` d'Automation, car il dépend entièrement d'un ensemble standard de commandes. Les commandes ont rarement des arguments, et aucune information de type n'est requise. (La cohérence des types est également réduite pour les arguments de commande).  
  
 Dans la conception d’interface de dispatch de commande, chaque commande appartient à un « groupe de commandes » qui est lui-même identifié avec un **GUID**. Par conséquent, une personne peut définir un nouveau groupe ainsi que toutes les commandes au sein de ce groupe sans avoir à coordonner avec Microsoft ou un autre fournisseur. (Il s’agit essentiellement les mêmes méthodes de définition comme un **dispinterface** plus **DISPID** dans Automation. Un chevauchement se produit ici, bien que ce mécanisme de routage de commande s'applique uniquement au routage de commande, et pas à la création de scripts et à la programmabilité à grande échelle, comme c'est le cas dans Automation).  
  
 `IOleCommandTarget` prend en charge les scénarios suivants :  
  
-   Lorsqu’un objet est activé, seules de barres d’outils sont généralement affichées et barres d’outils de l’objet peuvent comporter des boutons pour certaines commandes de conteneur comme place **impression**, **Aperçu avant impression**,  **Enregistrer**, **nouveau**, **Zoom**et d’autres. (Les normes d'activation sur place recommandent que les objets suppriment ces boutons de leurs barres d'outils, ou au moins les désactivent. Cette conception permet l'activation et le routage de ces commandes vers le gestionnaire approprié). Actuellement, il n'existe aucun mécanisme permettant à l'objet de distribuer ces commandes au conteneur.  
  
-   Lorsqu’un document actif est incorporé dans un conteneur de documents actifs (par exemple, le classeur Office), le conteneur peut avoir besoin envoyer des commandes telles que **impression**, **mise en Page**, **propriétés**et d’autres pour le document actif contenu.  
  
 Le routage de commande simple peut être géré via les normes Automation existantes et `IDispatch`. Toutefois, la surcharge liée à `IDispatch` est supérieure à la valeur requise ici, `IOleCommandTarget` fournit donc un moyen plus simple d'atteindre les mêmes objectifs :  
  
```  
interface IOleCommandTarget : IUnknown  
    {  
    HRESULT QueryStatus(  
        [in] GUID *pguidCmdGroup,  
        [in] ULONG cCmds,  
        [in,out][size_is(cCmds)] OLECMD *prgCmds,  
        [in,out] OLECMDTEXT *pCmdText);  
    HRESULT Exec(  
        [in] GUID *pguidCmdGroup,  
        [in] DWORD nCmdID,  
        [in] DWORD nCmdExecOpt,  
        [in] VARIANTARG *pvaIn,  
        [in,out] VARIANTARG *pvaOut);  
    }  
```  
  
 Le `QueryStatus` méthode ici teste si un ensemble particulier de commandes, le jeu identifié par un **GUID**, est pris en charge. Cet appel remplit un tableau de **OLECMD** valeurs (structures) avec la liste de prise en charge des commandes ainsi qu’un texte qui décrit le nom d’une information de commande et/ou d’état de retour. Lorsque l’appelant souhaite appeler une commande, il peut passer la commande (et le jeu **GUID**) à `Exec` avec les options et les arguments, pour obtenir une valeur de retour.  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneurs de documents actifs](../mfc/active-document-containers.md)

