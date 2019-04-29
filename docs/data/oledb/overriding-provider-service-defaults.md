---
title: Substitution des services par défaut du fournisseur
ms.date: 10/29/2018
helpviewer_keywords:
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
ms.openlocfilehash: 08011f65ca220885e124e5ad6072244e4ad6e80d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62282947"
---
# <a name="overriding-provider-service-defaults"></a>Substitution des services par défaut du fournisseur

Valeur de Registre du fournisseur pour les OLEDB_SERVICES est retournée en tant que la valeur par défaut pour le [DBPROP_INIT_OLEDBSERVICES](/previous-versions/windows/desktop/ms716898(v=vs.85)) propriété d’initialisation sur l’objet de source de données.

Tant que l’entrée de Registre existe, les objets du fournisseur sont agrégées. L’utilisateur peut remplacer le paramétrage par défaut des services activés en définissant la propriété DBPROP_INIT_OLEDBSERVICES avant l’initialisation. Pour activer ou désactiver un service particulier, l’utilisateur obtient la valeur actuelle de la propriété DBPROP_INIT_OLEDBSERVICES, définit ou efface le bit de la propriété particulière à être activé ou désactivé et réinitialise la propriété. DBPROP_INIT_OLEDBSERVICES peut être définie directement dans OLE DB ou dans la chaîne de connexion passée à ADO ou `IDataInitialize::GetDatasource`. Les valeurs correspondantes pour activer ou désactiver des services individuels sont répertoriés dans le tableau suivant.

|Services activés par défaut|Valeur de propriété DBPROP_INIT_OLEDBSERVICES|Valeur de chaîne de connexion|
|------------------------------|------------------------------------------------|--------------------------------|
|Tous les services (par défaut)|DBPROPVAL_OS_ENABLEALL|« Services OLE DB = -1 ; »|
|Tous sauf le regroupement et l’inscription automatique|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_RESOURCEPOOLING &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT`|"OLE DB Services = -4;"|
|Tout sauf le curseur Client|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"OLE DB Services = -5;"|
|Tous sauf le regroupement, l’inscription automatique et le curseur Client|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"OLE DB Services = -7;"|
|Aucun service|`~DBPROPVAL_OS_ENABLEALL`|"OLE DB Services = 0;"|

Si l’entrée de Registre n’existe pas pour le fournisseur, les gestionnaires de composants ne sont pas collecter les objets du fournisseur. Aucun service n’est activée, même si explicitement demandée par l’utilisateur.

## <a name="see-also"></a>Voir aussi

[Regroupement des ressources](/previous-versions/windows/desktop/ms713655(v=vs.85))<br/>
[Comment les consommateurs utilisent le regroupement des ressources](/previous-versions/windows/desktop/ms715907(v=vs.85))<br/>
[Comment les fournisseurs de travailler efficacement avec le regroupement de ressources](/previous-versions/windows/desktop/ms714906(v=vs.85))<br/>
[Activation et désactivation des services OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)<br/>