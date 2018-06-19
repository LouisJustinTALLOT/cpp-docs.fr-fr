---
title: Exemples de scripts de Registre | Documents Microsoft
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
ms.openlocfilehash: 4c192e8bec1d32dd7d7a7953e5da72a139c7520e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361887"
---
# <a name="registry-scripting-examples"></a>Exemples de scripts du Registre
Les exemples de script dans cette rubrique montrent comment ajouter une clé au Registre du système, inscrire le serveur Registrar COM et spécifier plusieurs arborescences d’analyse.  
  
## <a name="add-a-key-to-hkeycurrentuser"></a>Ajouter une clé dans HKEY_CURRENT_USER  
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
  
 À présent, le script ajoute une sous-clé, `HasASubkey`à `MyVeryOwnKey`. Cette sous-clé, il ajoute les deux le `PrettyCool` sous-clé (avec une valeur par défaut `DWORD` valeur de 55) et la `ANameValue` nommé valeur (avec une valeur de chaîne `WithANamedValue`).  
  
##  <a name="_atl_register_the_registrar_com_server"></a> Inscrire le serveur COM de bureau d’enregistrement  
 Le script suivant inscrit le serveur Registrar COM lui-même.  
  
```  
HKCR  
{  
    ATL.Registrar = s 'ATL Registrar Class'  
 {  
    CLSID = s '{44EC053A-400F-11D0-9DCD-00A0C90391D3}'  
 }  
    NoRemove CLSID  
 {  
    ForceRemove {44EC053A-400F-11D0-9DCD-00A0C90391D3} = 
    s 'ATL Registrar Class'  
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
  
 Au moment de l’exécution, cette arborescence d’analyse ajoute la `ATL.Registrar` clé `HKEY_CLASSES_ROOT`. Pour cette nouvelle clé ensuite :  
  
-   Spécifie `ATL Registrar Class` en tant que valeur de chaîne de la clé par défaut.  
  
-   Ajoute `CLSID` comme une sous-clé.  
  
-   Spécifie `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` pour `CLSID`. (Cette valeur est le bureau d’enregistrement CLSID pour une utilisation avec `CoCreateInstance`.)  
  
 Étant donné que `CLSID` est partagé, il ne doit être supprimé en mode de suppression de l’inscription. L’instruction, `NoRemove CLSID`, fait cela en indiquant que `CLSID` doit être ouvert en mode inscription et ignoré en mode de suppression de l’inscription.  
  
 La `ForceRemove` instruction fournit une fonction de nettoyage en supprimant une clé et toutes ses sous-clés avant de recréer la clé. Cela peut être utile si les noms des sous-clés ont changé. Dans cet exemple de script, `ForceRemove` vérifie si `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` existe déjà. Dans ce cas, `ForceRemove`:  
  
-   Supprime de manière récursive `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` et toutes ses sous-clés.  
  
-   Recrée `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.  
  
-   Ajoute `ATL Registrar Class` en tant que valeur de chaîne par défaut pour `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.  
  
 L’arborescence d’analyse ajoute à présent deux nouvelles sous-clés à `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`. La première clé `ProgID`, obtient une valeur de chaîne par défaut est le ProgID. La deuxième clé, `InprocServer32`, obtient une valeur de chaîne par défaut, `%MODULE%`, qui est la valeur du préprocesseur expliquée dans la section, [à l’aide des paramètres remplaçables (le préprocesseur de Registrar)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md), de cet article. `InprocServer32` Obtient également une valeur nommée, `ThreadingModel`, avec une valeur de chaîne `Apartment`.  
  
## <a name="specify-multiple-parse-trees"></a>Spécifier plusieurs arborescences d’analyse  
 Pour spécifier plus d’une arborescence d’analyse dans un script, vous devez simplement placer une arborescence à la fin d’un autre. Par exemple, le script suivant ajoute la clé, `MyVeryOwnKey`, pour les arborescences d’analyse pour les deux `HKEY_CLASSES_ROOT` et `HKEY_CURRENT_USER`:  
  
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
>  Dans un script de Registre, 4K est la taille maximale de jeton. (Un jeton est tout élément reconnaissable de la syntaxe.) Dans l’exemple de script précédent, `HKCR`, `HKEY_CURRENT_USER`, `'MyVeryOwnKey'`, et `'HowGoesIt'` sont tous des jetons.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de scripts d’inscription](../atl/creating-registrar-scripts.md)

