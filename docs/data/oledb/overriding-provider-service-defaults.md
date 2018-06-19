---
title: Par défaut du Service fournisseur de substitution | Documents Microsoft
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
ms.openlocfilehash: be802c1c3c6ba4b77d1418c9c620840e9ab10170
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33110078"
---
# <a name="overriding-provider-service-defaults"></a>Substitution des services par défaut du fournisseur
Valeur de Registre du fournisseur pour **OLEDB_SERVICES** est retourné en tant que la valeur par défaut pour le [DBPROP_INIT_OLEDBSERVICES](https://msdn.microsoft.com/en-us/library/ms716898.aspx) propriété d’initialisation de l’objet de source de données.  
  
 Tant que l’entrée de Registre existe, les objets du fournisseur sont agrégées et que l’utilisateur peut remplacer le paramétrage par défaut des services activés en définissant le **DBPROP_INIT_OLEDBSERVICES** propriété avant l’initialisation. Pour activer ou désactiver un service particulier, l’utilisateur obtient généralement la valeur actuelle de la **DBPROP_INIT_OLEDBSERVICES** propriété, définit ou supprime le bit pour la propriété d’être activés ou désactivés et réinitialise la propriété. **DBPROP_INIT_OLEDBSERVICES** peut être définie directement dans OLE DB ou dans la chaîne de connexion passée à ADO ou **IDataInitialize::GetDatasource**. Les valeurs correspondantes pour activer ou désactiver des services individuels sont répertoriés dans le tableau suivant.  
  
|Services activés par défaut|Valeur de la propriété DBPROP_INIT_OLEDBSERVICES|Valeur de chaîne de connexion|  
|------------------------------|------------------------------------------------|--------------------------------|  
|Tous les services (par défaut)|**DBPROPVAL_OS_ENABLEALL**|« Services OLE DB = -1 ; »|  
|Tous sauf le regroupement et l’inscription automatique|**DBPROPVAL_OS_ENABLEALL &AMP;**<br /><br /> **~ DBPROPVAL_OS_RESOURCEPOOLING &AMP;**<br /><br /> **~DBPROPVAL_OS_TXNENLISTMENT**|« Services OLE DB = -4 ; »|  
|Tous sauf le curseur Client|**DBPROPVAL_OS_ENABLEALL** &<br /><br /> ~**DBPROPVAL_OS_CLIENTCURSOR**|« Services OLE DB = -5 ; »|  
|Tous sauf le regroupement, l’inscription automatique et le curseur Client|**DBPROPVAL_OS_ENABLEALL &AMP;**<br /><br /> **~ DBPROPVAL_OS_TXNENLISTMENT &AMP;**<br /><br /> **~DBPROPVAL_OS_CLIENTCURSOR**|« Services OLE DB = -7 ; »|  
|Aucun service|~**DBPROPVAL_OS_ENABLEALL**|« Services OLE DB = 0 ; »|  
  
 Si l’entrée de Registre n’existe pas pour le fournisseur, les gestionnaires de composants ne regroupent pas les objets du fournisseur, et aucun service n’est appelé, même si explicitement demandée par l’utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Regroupement des ressources](https://msdn.microsoft.com/en-us/library/ms713655.aspx)   
 [Comment les consommateurs utilisent le regroupement des ressources](https://msdn.microsoft.com/en-us/library/ms715907.aspx)   
 [Comment les fournisseurs de travailler efficacement avec le regroupement des ressources](https://msdn.microsoft.com/en-us/library/ms714906.aspx)   
 [Activation et désactivation des services OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)