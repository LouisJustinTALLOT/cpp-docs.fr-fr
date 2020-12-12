---
description: 'En savoir plus sur les éléments suivants : date et heure'
title: Date et heure
ms.date: 08/13/2019
helpviewer_keywords:
- time, MFC programming
- time
- MFC, date and time
- dates, MFC
ms.assetid: ecf56dc5-d418-4603-ad3e-af7e205a6403
ms.openlocfilehash: 4a8f2d5c9537f07c5d410361e79bf14a12778bc8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167030"
---
# <a name="date-and-time"></a>Date et heure

MFC prend en charge différentes façons d’utiliser des dates et des heures :

- Prise en charge du [type de données date](../atl-mfc-shared/date-type.md)Automation. La DATE prend en charge les valeurs de date, d’heure et de date/heure. Les classes [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) et [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) encapsulent cette fonctionnalité. Ils fonctionnent avec la classe [COleVariant](../mfc/reference/colevariant-class.md) à l’aide de la prise en charge d’Automation.

- Classes de temps à usage général. Les classes [ctime](../atl-mfc-shared/reference/ctime-class.md) et [CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md) encapsulent la plupart des fonctionnalités associées à la bibliothèque de temps ANSI-standard, qui est déclarée dans Time. H.

- Prise en charge de l’horloge système. Avec la version 3,0 de MFC, la prise en charge a été ajoutée à `CTime` pour les `SYSTEMTIME` types de données Win32 et `FILETIME` .

## <a name="date-and-time-automation-support"></a>Date et heure : prise en charge d’Automation

La classe [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) offre un moyen de représenter des informations de date et d’heure. Elle offre une granularité plus fine et une plus grande plage que la classe [ctime](../atl-mfc-shared/reference/ctime-class.md) . La classe [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) représente le temps écoulé, par exemple la différence entre deux `COleDateTime` objets.

Les `COleDateTime` `COleDateTimeSpan` classes et sont conçues pour être utilisées avec la `COleVariant` classe. `COleDateTime` et `COleDateTimeSpan` sont également utiles dans la programmation de bases de données MFC, mais elles peuvent être utilisées chaque fois que vous souhaitez manipuler des valeurs de date et d’heure. Bien que la `COleDateTime` classe ait une plus grande plage de valeurs et une granularité plus fine que la `CTime` classe, elle nécessite davantage de stockage par objet que `CTime` . Il y a également quelques considérations particulières à prendre en compte lors de l’utilisation du type de DATE sous-jacent. Pour plus d’informations sur l’implémentation de DATE, consultez [le type date](../atl-mfc-shared/date-type.md).

`COleDateTime` les objets peuvent être utilisés pour représenter les dates comprises entre le 1er janvier 100 et le 31 décembre 9999. `COleDateTime` les objets sont des valeurs à virgule flottante, avec une résolution approximative de 1 milliseconde. `COleDateTime` est basé sur le type de données DATE, défini dans la documentation MFC sous [COleDateTime :: Operator date](../atl-mfc-shared/reference/coledatetime-class.md#operator_date). L’implémentation réelle de la DATE s’étend au-delà de ces limites. L' `COleDateTime` implémentation impose ces limites pour faciliter l’utilisation de la classe.

`COleDateTime` ne prend pas en charge les dates juliennes. Le calendrier grégorien est supposé s’étendre en arrière jusqu’au 1er janvier 100.

`COleDateTime` ignore l’heure d’été (DST). L’exemple de code suivant compare deux méthodes de calcul d’un intervalle de temps qui dépasse la date de basculement de l’heure d’été : une utilisant la bibliothèque CRT et l’autre à l’aide de `COleDateTime` .

La première méthode définit deux `CTime` objets, *time1* et *TIME2 ?*, respectivement les 5 avril et 6 avril, à l’aide des structures de type C standard `tm` et `time_t` . Le code affiche *time1* et *TIME2 ?* et l’intervalle de temps entre eux.

La deuxième méthode crée deux `COleDateTime` objets, `oletime1` et `oletime2` , et les affecte aux mêmes dates que *time1* et *TIME2 ?*. Il affiche `oletime1` et `oletime2` et l’intervalle de temps entre eux.

La bibliothèque CRT calcule correctement une différence de 23 heures. `COleDateTimeSpan` calcule une différence de 24 heures.

[!code-cpp[NVC_ATLMFC_Utilities#176](../atl-mfc-shared/codesnippet/cpp/date-and-time-automation-support_1.cpp)]

### <a name="get-the-current-time"></a>Obtenir l'heure actuelle

La procédure suivante montre comment créer un `COleDateTime` objet et l’initialiser avec l’heure actuelle.

#### <a name="to-get-the-current-time"></a>Pour accéder à l’heure actuelle

1. Créez un objet `COleDateTime`.

1. Appelez `GetCurrentTime`.

   [!code-cpp[NVC_ATLMFC_Utilities#177](../atl-mfc-shared/codesnippet/cpp/current-time-automation-classes_1.cpp)]

### <a name="calculate-elapsed-time"></a>Calculer le temps écoulé

Cette procédure montre comment calculer la différence entre deux `COleDateTime` objets et obtenir un `COleDateTimeSpan` résultat.

#### <a name="to-calculate-elapsed-time"></a>Pour calculer le temps écoulé

1. Créez deux `COleDateTime` objets.

1. Affectez à l’un des `COleDateTime` objets l’heure actuelle.

1. Effectuer une tâche longue.

1. Affectez à l’autre `COleDateTime` objet l’heure actuelle.

1. Prenez la différence entre les deux fois.

   [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/cpp/elapsed-time-automation-classes_1.cpp)]

### <a name="format-a-time"></a>Mettre en forme une heure

#### <a name="to-format-a-time"></a>Pour mettre en forme une heure

Utilisez la `Format` fonction membre de [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) ou de [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) pour créer une chaîne de caractères représentant l’heure ou le temps écoulé.

   [!code-cpp[NVC_ATLMFC_Utilities#179](../atl-mfc-shared/codesnippet/cpp/formatting-time-automation-classes_1.cpp)]

Pour plus d’informations, consultez la classe [COleVariant](../mfc/reference/colevariant-class.md).

## <a name="date-and-time-database-support"></a>Date et heure : prise en charge des bases de données

À partir de la version 4,0, la programmation de bases de données MFC utilise les classes [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) et [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) pour représenter les données de date et d’heure. Ces classes, également utilisées dans Automation, sont dérivées de la classe [COleVariant](../mfc/reference/colevariant-class.md). Ils offrent une meilleure prise en charge de la gestion des données de date et d’heure que celles de [ctime](../atl-mfc-shared/reference/ctime-class.md) et [CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md).

## <a name="date-and-time-systemtime-support"></a>Date et heure : prise en charge de SYSTEMTIME

La classe [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) a des constructeurs qui acceptent les heures système et de fichier de Win32.

La `FILETIME` structure Win32 représente l’heure sous la forme d’une valeur 64 bits. Il s’agit d’un format plus commode pour le stockage interne qu’une `SYSTEMTIME` structure, et le format utilisé par Win32 pour représenter l’heure de création du fichier. Pour plus d’informations sur la structure SYSTEMTIME, consultez [SystemTime](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime). Pour plus d’informations sur la structure FILETIME, consultez [fileTime](/windows/desktop/api/minwinbase/ns-minwinbase-filetime).

## <a name="see-also"></a>Voir aussi

[Relatifs](../mfc/mfc-concepts.md)\
[Rubriques générales sur MFC](../mfc/general-mfc-topics.md)
