---
title: Test de votre fournisseur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, testing
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c35b1391e5b8cbfb073255b3680b0376d19ae040
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33104787"
---
# <a name="testing-your-provider"></a>Test de votre fournisseur
Avant de libérer un fournisseur, vous devez effectuer les tests suivants, dans l’ordre indiqué. Ces tests vous assurer que les fonctions du fournisseur correctement pour la plupart des utilisateurs potentiels.  
  
1.  Test du fournisseur en utilisant un [consommateur](../../data/oledb/creating-an-ole-db-consumer.md) application écrite avec les modèles du consommateur OLE DB. Le consommateur de test doit couvrir tous les domaines fonctionnels de votre fournisseur (tout le code que vous avez ajouté ou modifié).  
  
2.  Testez le fournisseur à l’aide d’une application consommateur écrite avec ADO. La plupart des développeurs (notamment les développeurs Microsoft Visual Basic et Microsoft c#) utilisent ADO ou ADO.NET pour les applications consommateurs. Le consommateur de test doit couvrir tous les domaines fonctionnels de votre fournisseur. Pour obtenir un exemple d’application consommateur ADO, consultez [exemples de Code ADO dans Microsoft Visual Basic](https://msdn.microsoft.com/en-us/library/ms807514.aspx).  
  
3.  Exécutez les tests de compatibilité OLE DB (y compris les tests de compatibilité ADO) pour vous assurer que votre fournisseur est conforme au niveau 0 standard pour les fournisseurs OLE DB. (Pour obtenir une explication du niveau 0, recherchez « OLE DB Level 0 Conformance Tests » à [Guide du programmeur OLE DB](http://go.microsoft.com/fwlink/p/?linkid=121548). Ces tests et la documentation associée sont inclus avec Visual C++ dans le Kit de développement accès aux données. Ces tests vous aident aussi à vous assurer que votre fournisseur s’exécute correctement lorsqu’il est regroupé par d’autres [fournisseurs de services](../../data/oledb/ole-db-resource-pooling-and-services.md) et sont particulièrement utiles si vous modifiez ou ajoutez des propriétés. Pour plus d’informations sur les tests de compatibilité, consultez le fichier Readme pour Data Access SDK, qui se trouve sur l’un des CD-ROM Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des modèles du fournisseur OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)