---
title: Utilisation des documents et vues
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], documents
- MFC [C++], views
- views [C++], MFC
- documents [C++], MFC
ms.assetid: 349b142d-1c5a-4b99-9de4-241e41d3d2f1
ms.openlocfilehash: c7622c8ffe9e3c41d33ddf984fc9df6661c3a857
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432082"
---
# <a name="working-with-documents-and-views"></a>Utilisation des documents et vues

La bibliothèque Microsoft Foundation Classes (MFC) s’appuie sur l’architecture document/vue pour la plupart de ses fonctionnalités. En règle générale, un document stocke vos données et une vue, il s’affiche dans la zone cliente d’une fenêtre frame et gère l’interaction utilisateur avec les données. La vue communique avec le document pour obtenir et mettre à jour les données. Vous pouvez utiliser les classes de base de données avec l’infrastructure ou sans lui.

Pour plus d’informations sur l’utilisation de classes de base de données dans le framework, consultez [MFC : utilisation de Classes de base de données des Documents et vues](../../data/mfc-using-database-classes-with-documents-and-views.md).

Par défaut, l’Assistant Application MFC crée une application squelette sans prise en charge de la base de données. Toutefois, vous pouvez sélectionner des options permettant d’inclure la prise en charge de la base de données minimale ou plus complète prise en charge en fonction du formulaire. Pour plus d’informations sur les options de l’Assistant application, consultez [prise en charge de la base de données, Assistant Application MFC](../../mfc/reference/database-support-mfc-application-wizard.md).

Vous pouvez également utiliser les classes de base de données sans utiliser l’architecture document/vue complète. Pour plus d’informations, consultez [MFC : à l’aide de Classes de base de données sans document ni vue](../../data/mfc-using-database-classes-without-documents-and-views.md).

## <a name="see-also"></a>Voir aussi

[ODBC et MFC](../../data/odbc/odbc-and-mfc.md)