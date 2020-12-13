---
description: 'En savoir plus sur : présentation des arborescences d’analyse'
title: Bureaux d’enregistrement ATL et arborescences d’analyse
ms.date: 11/04/2016
helpviewer_keywords:
- parse trees
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
ms.openlocfilehash: cae5256bf932478135db747f80816378e61429a0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138240"
---
# <a name="understanding-parse-trees"></a>Comprendre les arborescences d’analyse

Vous pouvez définir un ou plusieurs arbres d’analyse dans le script de votre registraire, où chaque arborescence d’analyse se présente sous la forme suivante :

> \<root key>{\<registry expression>}+

où :

> \<root key> :: = HKEY_CLASSES_ROOT \| HKEY_CURRENT_USER \|\
> &emsp;HKEY_LOCAL_MACHINE \| HKEY_USERS \|\
> &emsp;HKEY_PERFORMANCE_DATA \| HKEY_DYN_DATA \|\
> &emsp;HKEY_CURRENT_CONFIG \| HKCR de HKCR \|\|\
> &emsp;HKLM \| HKU \| HKPD \| HKDD \| HKCC

> \<registry expression>::= \<Add Key> \|\<Delete Key>

> \<Add Key>:: = \[ **ForceRemove** \| **NoRemove** \| **Val**] \<Key Name> [ \<Key Value> ] [{ \<Add Key> }]

> \<Delete Key> :: = **Supprimer**\<Key Name>

> \<Key Name> ::= **'**\<AlphaNumeric>+**'**

> \<AlphaNumeric> :: = *n’importe quel caractère non null, c.-à-d. ASCII 0*

> \<Key Value> ::= \<Key Type>\<Key Name>

> \<Key Type> :: = **s** \| **d**

> \<Key Value> ::= **'**\<AlphaNumeric>**'**

> [!NOTE]
> `HKEY_CLASSES_ROOT` et `HKCR` sont équivalents ; `HKEY_CURRENT_USER` et `HKCU` sont équivalents, et ainsi de suite.

Une arborescence d’analyse peut ajouter plusieurs clés et sous-clés à \<root key> . Dans ce cas, elle garde le handle d’une sous-clé ouverte jusqu’à ce que l’analyseur ait terminé d’analyser toutes ses sous-clés. Cette approche est plus efficace que l’utilisation d’une seule clé à la fois, comme illustré dans l’exemple suivant :

```rgs
HKEY_CLASSES_ROOT
{
    'MyVeryOwnKey'
    {
        'HasASubKey'
        {
            'PrettyCool'
        }
    }
}
```

Ici, le Bureau d’enregistrement s’ouvre pour la première fois (crée) `HKEY_CLASSES_ROOT\MyVeryOwnKey` . Il voit ensuite que `MyVeryOwnKey` a une sous-clé. Au lieu de fermer la clé à `MyVeryOwnKey` , le Bureau d’enregistrement conserve le descripteur et l’ouvre (crée) `HasASubKey` à l’aide de ce handle parent. (Le registre système peut être plus lent quand aucun descripteur parent n’est ouvert.) Par conséquent, l’ouverture, puis l' `HKEY_CLASSES_ROOT\MyVeryOwnKey` ouverture `HasASubKey` avec `MyVeryOwnKey` en tant que parent est plus rapide que l’ouverture `MyVeryOwnKey` , la fermeture `MyVeryOwnKey` , puis l’ouverture `MyVeryOwnKey\HasASubKey` .

## <a name="see-also"></a>Voir aussi

[Création de scripts d’inscription](../atl/creating-registrar-scripts.md)
