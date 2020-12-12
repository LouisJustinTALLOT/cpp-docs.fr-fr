---
description: 'En savoir plus sur : objets de données et sources de données (OLE)'
title: Objets de données et sources de données (OLE)
ms.date: 11/04/2016
helpviewer_keywords:
- data objects [MFC], definition
- data transfer [MFC]
- OLE [MFC], data transfer
- data sources [MFC], definition
- data transfer [MFC], definition
- OLE [MFC], data objects
- OLE [MFC], data sources
ms.assetid: 8f68eed8-0ce8-4489-a4cc-f95554f89090
ms.openlocfilehash: 719053e2a75b18fbf54440403351198acc66b9d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291205"
---
# <a name="data-objects-and-data-sources-ole"></a>Objets de données et sources de données (OLE)

Lorsque vous effectuez un transfert de données, soit à l’aide du presse-papiers, soit en effectuant un glisser-déplacer, les données ont une source et une destination. Une application fournit les données pour la copie, et une autre application l’accepte pour le collage. Chaque côté du transfert doit effectuer des opérations différentes sur les mêmes données pour que le transfert aboutisse. La bibliothèque MFC (Microsoft Foundation Class) fournit deux classes qui représentent chaque côté de ce transfert :

- Les sources de données (implémentées par les `COleDataSource` objets) représentent le côté source du transfert de données. Elles sont créées par l’application source lorsque les données doivent être copiées dans le presse-papiers, ou lorsque les données sont fournies pour une opération de glisser-déplacer.

- Les objets de données (implémentés par les `COleDataObject` objets) représentent le côté destination du transfert de données. Ils sont créés lorsque des données sont déposées dans l’application de destination, ou lorsqu’il est demandé d’effectuer une opération de collage à partir du presse-papiers.

Les articles suivants expliquent comment utiliser des objets de données et des sources de données dans vos applications. Ces informations s’appliquent aux applications conteneur et serveur, car elles peuvent être appelées sur pour copier et coller des données.

- [Objets de données et sources de données : création et destruction](data-objects-and-data-sources-creation-and-destruction.md)

- [Objets de données et sources de données : manipulation](data-objects-and-data-sources-manipulation.md)

## <a name="in-this-section"></a>Dans cette section

[Glisser-déposer](drag-and-drop-ole.md)

[Presse-papiers](clipboard.md)

## <a name="see-also"></a>Voir aussi

[OLE](ole-in-mfc.md)<br/>
[COleDataObject, classe](reference/coledataobject-class.md)<br/>
[COleDataSource, classe](reference/coledatasource-class.md)
