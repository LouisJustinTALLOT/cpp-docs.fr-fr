---
title: Bureaux d’enregistrement ATL et arborescences d’analyse
ms.date: 11/04/2016
helpviewer_keywords:
- parse trees
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
ms.openlocfilehash: de2cea9b0e7b7c62236f708f9aa8217eaa5df51d
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168694"
---
# <a name="understanding-parse-trees"></a>Comprendre les arborescences d’analyse

Vous pouvez définir un ou plusieurs arbres d’analyse dans le script de votre registraire, où chaque arborescence d’analyse se présente sous la forme suivante :

> \<clé racine> {\<expression de Registre>} +

où :

> \<> de la clé racine :: = HKEY_CLASSES_ROOT | HKEY_CURRENT_USER | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKEY_LOCAL_MACHINE | HKEY_USERS | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKEY_PERFORMANCE_DATA | HKEY_DYN_DATA | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKEY_CURRENT_CONFIG | HKCR | HKCU | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKLM | HKU | HKPD | HKDD | HKCC

> \<expression de Registre> :: \<= Add Key> | \<Supprimer la clé>

> \<Ajout de clé> :: =**[ForceRemove** | **NoRemove** | **Val**]\<nom de clé\<> [valeur de clé>\<] [{Add Key>}]

> \<Supprimer la clé> :: = **supprimer**\<le nom de la clé>

> \<Nom de clé> :: = **'**\<alphanumérique>+**'**

> \<Alphanumérique> :: = *n’importe quel caractère non null, c.-à-d. ASCII 0*

> \<Valeur de clé> :: \<= type de \<clé>nom de clé>

> \<Type de clé> :: = **s** | **d**

> \<Valeur de clé> :: = **'**\<>alphanumériques **'**

> [!NOTE]
> `HKEY_CLASSES_ROOT`et `HKCR` sont équivalents ; `HKEY_CURRENT_USER` et `HKCU` sont équivalents ; et ainsi de suite.

Une arborescence d’analyse peut ajouter plusieurs clés et sous-clés \<à la clé racine>. Dans ce cas, elle garde le handle d’une sous-clé ouverte jusqu’à ce que l’analyseur ait terminé d’analyser toutes ses sous-clés. Cette approche est plus efficace que l’utilisation d’une seule clé à la fois, comme illustré dans l’exemple suivant :

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

Ici, le Bureau d’enregistrement s’ouvre pour `HKEY_CLASSES_ROOT\MyVeryOwnKey`la première fois (crée). Il voit ensuite que `MyVeryOwnKey` a une sous-clé. Au lieu de fermer la clé `MyVeryOwnKey`à, le Bureau d’enregistrement conserve le descripteur et `HasASubKey` l’ouvre (crée) à l’aide de ce handle parent. (Le registre système peut être plus lent quand aucun descripteur parent n’est ouvert.) Par conséquent, `HKEY_CLASSES_ROOT\MyVeryOwnKey` l’ouverture, `HasASubKey` puis `MyVeryOwnKey` l’ouverture avec en tant que parent `MyVeryOwnKey`est plus `MyVeryOwnKey`rapide que l’ouverture `MyVeryOwnKey\HasASubKey`, la fermeture, puis l’ouverture.

## <a name="see-also"></a>Voir aussi

[Création de scripts d’inscription](../atl/creating-registrar-scripts.md)
