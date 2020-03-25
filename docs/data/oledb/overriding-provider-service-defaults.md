---
title: Substitution des services par défaut du fournisseur
ms.date: 10/29/2018
helpviewer_keywords:
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
ms.openlocfilehash: 4cf3ad1064627f64315822a5045642aa50330d10
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209801"
---
# <a name="overriding-provider-service-defaults"></a>Substitution des services par défaut du fournisseur

La valeur de Registre du fournisseur pour OLEDB_SERVICES est retournée en tant que valeur par défaut pour la propriété d’initialisation [DBPROP_INIT_OLEDBSERVICES](/previous-versions/windows/desktop/ms716898(v=vs.85)) sur l’objet de source de données.

Tant que l’entrée de Registre existe, les objets du fournisseur sont agrégés. L’utilisateur peut remplacer le paramètre par défaut du fournisseur pour les services activés en définissant la propriété DBPROP_INIT_OLEDBSERVICES avant l’initialisation. Pour activer ou désactiver un service particulier, l’utilisateur obtient la valeur actuelle de la propriété DBPROP_INIT_OLEDBSERVICES, définit ou efface le bit pour la propriété particulière à activer ou désactiver, puis réinitialise la propriété. DBPROP_INIT_OLEDBSERVICES peut être défini directement dans OLE DB ou dans la chaîne de connexion transmise à ADO ou `IDataInitialize::GetDatasource`. Les valeurs correspondantes pour activer ou désactiver des services individuels sont répertoriées dans le tableau suivant.

|Services par défaut activés|Valeur de la propriété DBPROP_INIT_OLEDBSERVICES|Valeur dans la chaîne de connexion|
|------------------------------|------------------------------------------------|--------------------------------|
|Tous les services (par défaut)|DBPROPVAL_OS_ENABLEALL|« Services OLE DB =-1 ; »|
|Tout sauf le regroupement et l’inscription|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_RESOURCEPOOLING &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT`|« Services OLE DB =-4 ; »|
|Tout sauf le curseur client|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|« Services OLE DB =-5 ; »|
|Tout sauf le regroupement, l’inscription et le curseur client|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|« Services OLE DB =-7 ; »|
|Aucun service|`~DBPROPVAL_OS_ENABLEALL`|« Services OLE DB = 0 ; »|

Si l’entrée de Registre n’existe pas pour le fournisseur, les gestionnaires de composants ne recueilleront pas les objets du fournisseur. Aucun service n’est activé, même s’il est demandé explicitement par l’utilisateur.

## <a name="see-also"></a>Voir aussi

[Regroupement des ressources](/previous-versions/windows/desktop/ms713655(v=vs.85))<br/>
[Utilisation du regroupement des ressources par les consommateurs](/previous-versions/windows/desktop/ms715907(v=vs.85))<br/>
[Fonctionnement efficace des fournisseurs avec le regroupement de ressources](/previous-versions/windows/desktop/ms714906(v=vs.85))<br/>
[Activation et désactivation des services OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)<br/>
