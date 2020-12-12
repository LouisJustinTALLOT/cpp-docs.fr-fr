---
description: 'En savoir plus sur : test de votre fournisseur'
title: Test de votre fournisseur
ms.date: 10/29/2018
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, testing
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
ms.openlocfilehash: de9ba1b6cb66df8041cc6a94f357d52fc2194553
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272654"
---
# <a name="testing-your-provider"></a>Test de votre fournisseur

Avant de libérer un fournisseur, vous devez effectuer les tests suivants, dans l’ordre indiqué. Ces tests montrent que le fournisseur fonctionne correctement pour la plupart des utilisateurs potentiels.

1. Testez le fournisseur à l’aide d’une application [cliente](../../data/oledb/creating-an-ole-db-consumer.md) écrite avec les modèles de consommateur OLE DB. Le consommateur de test doit couvrir toutes les zones fonctionnelles de votre fournisseur (tout le code que vous avez ajouté ou modifié).

1. Testez le fournisseur à l’aide d’une application cliente écrite avec ADO. La plupart des développeurs (surtout les développeurs Microsoft Visual Basic et Microsoft C#) utilisent ADO ou ADO.NET pour les applications grand public. Le consommateur de test doit couvrir toutes les zones fonctionnelles de votre fournisseur. Pour obtenir un exemple d’application de consommateur ADO, consultez [exemples de code ADO dans Microsoft Visual Basic](/previous-versions/ms807514(v=msdn.10)).

1. Exécutez les tests de conformité OLE DB (y compris les tests de conformité ADO) pour indiquer que votre fournisseur est conforme à la norme de niveau 0 pour les fournisseurs de OLE DB. (Pour obtenir une explication du niveau 0, recherchez **OLE DB tests de conformité de niveau 0** à [OLE DB Guide du programmeur](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming). Ces tests et la documentation associée sont inclus avec Visual C++ dans le kit de développement logiciel (SDK) Data Access. Ces tests permettent également d’indiquer que votre fournisseur s’exécute correctement lorsqu’il est agrégé par d’autres [fournisseurs de services](../../data/oledb/ole-db-resource-pooling-and-services.md) et qu’il est particulièrement utile si vous modifiez ou ajoutez des propriétés. Pour plus d’informations sur les tests de conformité, consultez le fichier Lisez-moi du kit de développement logiciel (SDK) d’accès aux données, qui se trouve sur l’un des CD de Visual Studio.

## <a name="see-also"></a>Voir aussi

[Utilisation des modèles de fournisseur OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
