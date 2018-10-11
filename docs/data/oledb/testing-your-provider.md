---
title: Test de votre fournisseur | Microsoft Docs
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
ms.openlocfilehash: 04687ed080013d9ae96a11eda32e060c02c61dec
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49081979"
---
# <a name="testing-your-provider"></a>Test de votre fournisseur

Avant de publier un fournisseur, vous devez effectuer les tests suivants, dans l’ordre indiqué. Ces tests permettent de garantir le fonctionnement du fournisseur correctement pour la plupart des utilisateurs potentiels.  
  
1. Test du fournisseur en utilisant un [consommateur](../../data/oledb/creating-an-ole-db-consumer.md) application écrite avec les modèles du consommateur OLE DB. Le consommateur de test doit couvrir toutes les zones fonctionnelles de votre fournisseur (tout le code que vous avez ajouté ou modifié).  
  
1. Tester le fournisseur à l’aide d’une application consommateur écrite avec ADO. La plupart des développeurs (notamment les développeurs Microsoft Visual Basic et Microsoft c#) utilisent ADO ou ADO.NET pour les applications grand public. Le consommateur de test doit couvrir toutes les zones fonctionnelles de votre fournisseur. Pour obtenir un exemple d’application consommateur ADO, consultez [exemples de Code ADO dans Microsoft Visual Basic](https://msdn.microsoft.com/library/ms807514.aspx).  
  
1. Exécutez les tests de compatibilité OLE DB (y compris les tests de compatibilité ADO) pour vous assurer que votre fournisseur est conforme au niveau 0 standard pour les fournisseurs OLE DB. (Pour une explication du niveau 0, recherchez « OLE DB Level 0 Conformance Tests » sur [Guide du programmeur OLE DB](/previous-versions/windows/desktop/ms713643). Ces tests et la documentation associée sont inclus avec Visual C++ dans le Kit de développement accès aux données. Ces tests permettent également de vous assurer que votre fournisseur s’exécute bien lorsqu’il est regroupé par d’autres [fournisseurs de services](../../data/oledb/ole-db-resource-pooling-and-services.md) et sont particulièrement utiles si vous modifiez ou ajoutez des propriétés. Pour plus d’informations sur les tests de compatibilité, consultez le fichier Lisez-moi pour Data Access SDK, qui se trouve sur l’un des CD Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  

[Utilisation des modèles du fournisseur OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)