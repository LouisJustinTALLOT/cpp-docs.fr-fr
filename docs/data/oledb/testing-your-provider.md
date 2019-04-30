---
title: Test de votre fournisseur
ms.date: 10/29/2018
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, testing
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
ms.openlocfilehash: d7a3adad546834e2bdc80a695f4c3bf2259dc0ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389123"
---
# <a name="testing-your-provider"></a>Test de votre fournisseur

Avant de publier un fournisseur, vous devez effectuer les tests suivants, dans l’ordre indiqué. Ces tests montrent que les fonctions de fournisseur correctement pour la plupart des utilisateurs potentiels.

1. Test du fournisseur en utilisant un [consommateur](../../data/oledb/creating-an-ole-db-consumer.md) application écrite avec les modèles du consommateur OLE DB. Le consommateur de test doit couvrir toutes les zones fonctionnelles de votre fournisseur (tout le code que vous avez ajouté ou modifié).

1. Tester le fournisseur à l’aide d’une application consommateur écrite avec ADO. La plupart des développeurs (notamment les développeurs Microsoft Visual Basic et Microsoft c#) utilisent ADO ou ADO.NET pour les applications grand public. Le consommateur de test doit couvrir toutes les zones fonctionnelles de votre fournisseur. Pour obtenir un exemple d’application consommateur ADO, consultez [exemples de Code ADO dans Microsoft Visual Basic](https://msdn.microsoft.com/library/ms807514.aspx).

1. Exécutez les tests de compatibilité OLE DB (y compris les tests de compatibilité ADO) pour indiquer que votre fournisseur est conforme au niveau 0 standard pour les fournisseurs OLE DB. (Pour une explication du niveau 0, recherchez **Tests de compatibilité OLE DB de niveau 0** à [Guide du programmeur OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming). Ces tests et la documentation associée sont inclus avec Visual C++ dans le Kit de développement accès aux données. Ces tests permettent également de montrer que votre fournisseur s’exécute bien lorsqu’il est regroupé par d’autres [fournisseurs de services](../../data/oledb/ole-db-resource-pooling-and-services.md) et sont particulièrement utiles si vous modifiez ou ajoutez des propriétés. Pour plus d’informations sur les tests de compatibilité, consultez le fichier Lisez-moi pour Data Access SDK, qui se trouve sur l’un des CD Visual Studio.

## <a name="see-also"></a>Voir aussi

[Utilisation des modèles du fournisseur OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)