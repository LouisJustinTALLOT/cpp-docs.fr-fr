---
title: Exemples de script de Registre | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6dc28d8a0d5dc24d0f0c665e5a17fc38e0c9d08f
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753147"
---
# <a name="registry-scripting-examples"></a>Exemples de scripts du Registre

Les exemples de script dans cette rubrique montrent comment ajouter une clé dans le Registre système, inscrire le serveur de bureau d’enregistrement COM et spécifier plusieurs arborescences d’analyse.

## <a name="add-a-key-to-hkeycurrentuser"></a>Ajouter une clé à HKEY_CURRENT_USER

L’arborescence d’analyse suivante illustre un script simple qui ajoute une clé unique dans le Registre système. En particulier, le script ajoute la clé, `MyVeryOwnKey`à `HKEY_CURRENT_USER`. Il affecte également la valeur de chaîne par défaut `HowGoesIt` à la nouvelle clé :

```  
HKEY_CURRENT_USER  
{  
'MyVeryOwnKey' = s 'HowGoesIt'  
}  
```

Ce script peut facilement être étendu pour définir plusieurs sous-clés comme suit :

```  
HKCU  
{  
    'MyVeryOwnKey' = s 'HowGoesIt'  
    {  
        'HasASubkey'  
        {  
            'PrettyCool' = d '55'  
            val 'ANameValue' = s 'WithANamedValue'  
        }  
    }  
}  
```

À présent, le script ajoute une sous-clé, `HasASubkey`à `MyVeryOwnKey`. Cette sous-clé, il ajoute les deux le `PrettyCool` sous-clé (avec une valeur par défaut `DWORD` valeur de 55) et le `ANameValue` nommée value (avec une valeur de chaîne `WithANamedValue`).

##  <a name="_atl_register_the_registrar_com_server"></a> Inscrire le serveur COM de bureau d’enregistrement

Le script suivant inscrit le serveur de bureau d’enregistrement COM proprement dit.

```  
HKCR  
{  
    ATL.Registrar = s 'ATL Registrar Class'  
    {  
        CLSID = s '{44EC053A-400F-11D0-9DCD-00A0C90391D3}'  
    }  
    NoRemove CLSID  
    {  
        ForceRemove {44EC053A-400F-11D0-9DCD-00A0C90391D3} = s 'ATL Registrar Class'  
        {  
            ProgID = s 'ATL.Registrar'  
            InprocServer32 = s '%MODULE%'  
            {  
                val ThreadingModel = s 'Apartment'  
            }  
        }  
    }  
}  
```

Au moment de l’exécution, cette arborescence d’analyse ajoute la `ATL.Registrar` clé à `HKEY_CLASSES_ROOT`. Pour cette nouvelle clé, puis informatique :

- Spécifie `ATL Registrar Class` en tant que valeur de chaîne de la clé par défaut.

- Ajoute `CLSID` comme une sous-clé.

- Spécifie `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` pour `CLSID`. (Cette valeur est le bureau d’enregistrement CLSID pour une utilisation avec `CoCreateInstance`.)

Étant donné que `CLSID` est partagé, il ne doit être supprimé en mode d’annuler l’inscription. L’instruction, `NoRemove CLSID`, effectue cette opération en indiquant que `CLSID` doit être ouvert en mode de Registre et ignorés en mode d’annuler l’inscription.

La `ForceRemove` instruction fournit une fonction de nettoyage en supprimant une clé et toutes ses sous-clés avant de recréer la clé. Cela peut être utile si les noms des sous-clés ont changé. Dans cet exemple de script, `ForceRemove` vérifie si `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` existe déjà. Le cas échéant, `ForceRemove`:

- Supprime de manière récursive `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` et toutes ses sous-clés.

- Recrée `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.

- Ajoute `ATL Registrar Class` en tant que la valeur de chaîne par défaut `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.

L’arborescence d’analyse ajoute à présent deux nouvelles sous-clés à `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`. La première clé `ProgID`, obtient une valeur de chaîne par défaut est le ProgID. La deuxième clé, `InprocServer32`, obtient une valeur de chaîne par défaut, `%MODULE%`, qui est une valeur de préprocesseur est expliqué dans la section, [à l’aide des paramètres remplaçables (le préprocesseur de Registrar)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md), de cet article. `InprocServer32` Obtient également une valeur nommée, `ThreadingModel`, avec une valeur de chaîne `Apartment`.

## <a name="specify-multiple-parse-trees"></a>Spécifier plusieurs arborescences d’analyse

Pour spécifier plus d’une arborescence d’analyse dans un script, placez simplement un seul arbre à la fin d’un autre. Par exemple, le script suivant ajoute la clé, `MyVeryOwnKey`, aux arborescences d’analyse pour les deux `HKEY_CLASSES_ROOT` et `HKEY_CURRENT_USER`:

```  
HKCR  
{  
    'MyVeryOwnKey' = s 'HowGoesIt'  
}  
HKEY_CURRENT_USER  
{  
    'MyVeryOwnKey' = s 'HowGoesIt'  
}  
```

> [!NOTE]
> Dans un script de bureau d’enregistrement, 4K est la taille maximale de jeton. (Un jeton est tout élément reconnaissable de la syntaxe.) Dans l’exemple de script précédent, `HKCR`, `HKEY_CURRENT_USER`, `'MyVeryOwnKey'`, et `'HowGoesIt'` sont tous les jetons.

## <a name="see-also"></a>Voir aussi

[Création de scripts d’inscription](../atl/creating-registrar-scripts.md)

