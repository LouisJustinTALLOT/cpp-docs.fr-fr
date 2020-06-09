---
title: Gestion des messages et cibles des commandes
ms.date: 11/04/2016
f1_keywords:
- IOleCommandTarget
helpviewer_keywords:
- command targets [MFC]
- message handling [MFC], active documents
- IOleCommandTarget interface [MFC]
- command routing [MFC], command targets
ms.assetid: e45ce14c-e6b6-4262-8f3b-4e891e0ec2a3
ms.openlocfilehash: cbcbce1e476fef0d076f9c25b46b3166c1eb5935
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624350"
---
# <a name="message-handling-and-command-targets"></a>Gestion des messages et cibles des commandes

L'interface de dispatch de commande `IOleCommandTarget` définit un mécanisme simple et extensible pour interroger et exécuter des commandes. Ce mécanisme est plus simple qu’`IDispatch` d’Automation, car il dépend entièrement d’un ensemble standard de commandes. Les commandes ont rarement des arguments, et aucune information de type n’est requise. (La cohérence des types est également réduite pour les arguments de commande).

Dans la conception de l’interface de dispatch de commande, chaque commande appartient à un « groupe de commandes » qui est lui-même identifié par un **GUID**. Par conséquent, une personne peut définir un nouveau groupe ainsi que toutes les commandes au sein de ce groupe sans avoir à coordonner avec Microsoft ou un autre fournisseur. (Il s’agit essentiellement du même moyen de définition qu’une **dispinterface** et de **DISPID** dans Automation. Un chevauchement se produit ici, bien que ce mécanisme de routage de commande s'applique uniquement au routage de commande, et pas à la création de scripts et à la programmabilité à grande échelle, comme c'est le cas dans Automation).

`IOleCommandTarget` prend en charge les scénarios suivants :

- Lorsqu’un objet est activé sur place, seules les barres d’outils de l’objet sont généralement affichées et les barres d’outils de l’objet peuvent avoir des boutons pour certaines commandes de conteneur, telles que **Imprimer**, **Aperçu avant impression**, **Enregistrer**, **nouveau**, **Zoom**et autres. (Les normes d'activation sur place recommandent que les objets suppriment ces boutons de leurs barres d'outils, ou au moins les désactivent. Cette conception permet à ces commandes d’être activées et encore routées vers le gestionnaire approprié.) Actuellement, il n’existe aucun mécanisme permettant à l’objet de distribuer ces commandes au conteneur.

- Lorsqu’un document actif est incorporé dans un conteneur de documents actifs (tel qu’un classeur Office), le conteneur peut avoir besoin d’envoyer des commandes telles que l' **impression**, la **mise en page**, les **Propriétés**et d’autres éléments dans le document actif contenu.

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

La `QueryStatus` méthode vérifie ici si un ensemble particulier de commandes, le jeu identifié avec un **GUID**, est pris en charge. Cet appel remplit un tableau de valeurs **OLECMD** (structures) avec la liste des commandes prises en charge et retourne du texte décrivant le nom d’une commande et/ou des informations d’État. Lorsque l’appelant souhaite appeler une commande, il peut passer la commande (et le **GUID**du jeu) à `Exec` , ainsi qu’à des options et des arguments, en obtenant une valeur de retour.

## <a name="see-also"></a>Voir aussi

[Conteneurs de documents actifs](active-document-containers.md)
