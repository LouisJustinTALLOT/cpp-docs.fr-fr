---
title: Par défaut du Service fournisseur de substitution | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4cd51eaa06c8e9600b80d4a3cf6e192443105e65
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072185"
---
# <a name="overriding-provider-service-defaults"></a>Substitution des services par défaut du fournisseur

Valeur de Registre du fournisseur pour les OLEDB_SERVICES est retournée en tant que la valeur par défaut pour le [DBPROP_INIT_OLEDBSERVICES](/previous-versions/windows/desktop/ms716898) propriété d’initialisation sur l’objet de source de données.

Tant que l’entrée de Registre existe, les objets du fournisseur est agrégé et l’utilisateur peut remplacer le paramétrage par défaut des services activés en définissant le `DBPROP_INIT_OLEDBSERVICES` propriété avant l’initialisation. Pour activer ou désactiver un service particulier, l’utilisateur obtienne généralement la valeur actuelle de la `DBPROP_INIT_OLEDBSERVICES` propriété, définit ou efface le bit de la propriété particulière à être activé ou désactivé et réinitialise la propriété. `DBPROP_INIT_OLEDBSERVICES` peut être définie directement dans OLE DB ou dans la chaîne de connexion passée à ADO ou `IDataInitialize::GetDatasource`. Les valeurs correspondantes pour activer ou désactiver des services individuels sont répertoriés dans le tableau suivant.

|Services activés par défaut|Valeur de propriété DBPROP_INIT_OLEDBSERVICES|Valeur de chaîne de connexion|
|------------------------------|------------------------------------------------|--------------------------------|
|Tous les services (par défaut)|`DBPROPVAL_OS_ENABLEALL`|« Services OLE DB = -1 ; »|
|Tous sauf le regroupement et l’inscription automatique|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_RESOURCEPOOLING &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT`|« Services OLE DB = -4 ; »|
|Tout sauf le curseur Client|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|« Services OLE DB = -5 ; »|
|Tous sauf le regroupement, l’inscription automatique et le curseur Client|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|« Services OLE DB = -7 ; »|
|Aucun service|`~DBPROPVAL_OS_ENABLEALL`|« Services OLE DB = 0 ; »|

Si l’entrée de Registre n’existe pas pour le fournisseur, les gestionnaires de composants ne regroupent pas les objets du fournisseur, et aucun service n’est appelé, même si explicitement demandé par l’utilisateur.

## <a name="see-also"></a>Voir aussi

[Regroupement des ressources](/previous-versions/windows/desktop/ms713655)<br/>
[Comment les consommateurs utilisent le regroupement des ressources](/previous-versions/windows/desktop/ms715907)<br/>
[Comment les fournisseurs de travailler efficacement avec le regroupement de ressources](/previous-versions/windows/desktop/ms714906)<br/>
[Activation et désactivation des services OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)<br/>