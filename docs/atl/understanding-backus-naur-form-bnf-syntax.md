---
title: Enregistreur ATL et syntaxe BNF (Backus-Naur Form)
ms.date: 05/14/2019
helpviewer_keywords:
- BNF notation
- Backus-Naur form (BNF) syntax
ms.assetid: 994bbef0-9077-4aa8-bdfe-b7e830af9acc
ms.openlocfilehash: 0f07a39863b586d524d060dc3df7117e2c930b3e
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168707"
---
# <a name="understanding-backus-naur-form-bnf-syntax"></a>Présentation de la syntaxe BNF (Backus Nauer Form)

Les scripts utilisés par l’enregistreur ATL sont décrits dans cette rubrique avec la syntaxe BNF, qui utilise la notation indiquée dans le tableau suivant.

|Convention/symbole|Signification|
|------------------------|-------------|
|::=|Équivalent|
|&#124;|OR|
|X+|Un ou plusieurs X.|
|\[X]|X est facultatif. Les délimiteurs facultatifs sont indiqués par \[].|
|Du texte **en gras**|Un littéral de chaîne.|
|Du texte *en italique*|Comment construire le littéral de chaîne|

Comme indiqué dans le tableau précédent, les scripts d’enregistreur utilisent des littéraux de chaîne. Ces valeurs sont le texte réel qui doit apparaître dans votre script. Le tableau suivant décrit les littéraux de chaîne utilisés dans un script d’enregistreur ATL.

|Littéral de chaîne|Action|
|--------------------|------------|
|**ForceRemove**|Supprime complètement la clé suivante (si elle existe), puis la recrée.|
|**NoRemove**|Ne supprime pas la clé suivante lors de la désinscription.|
|**multiples**|Spécifie que `<Key Name>` est en réalité une valeur nommée.|
|**Supprimer**|Supprime la clé suivante lors de l’inscription.|
|**x**|Spécifie que la valeur suivante est une chaîne (REG_SZ).|
|**e**|Spécifie que la valeur suivante est un DWORD (REG_DWORD).|
|**lecteur**|Spécifie que la valeur suivante est une multichaîne (REG_MULTI_SZ).|
|**p**|Spécifie que la valeur suivante est une valeur binaire (REG_BINARY).|

## <a name="bnf-syntax-examples"></a>Exemples de syntaxe BNF

Voici quelques exemples de syntaxe pour vous aider à comprendre le fonctionnement de la notation et des littéraux de chaîne dans un script d’enregistreur ATL.

### <a name="syntax-example-1"></a>Exemple de syntaxe 1

> \<expression de Registre> :: \<= Add Key>

spécifie que `registry expression` équivaut à `Add Key`.

### <a name="syntax-example-2"></a>Exemple de syntaxe 2

> \<expression de Registre> :: \<= Add Key> | \<Supprimer la clé>

spécifie que `registry expression` équivaut à `Add Key` ou à `Delete Key`.

### <a name="syntax-example-3"></a>Exemple de syntaxe 3

> \<Nom de clé> :: =\<'alphanumérique>+ '

spécifie `Key Name` que est équivalent à une ou `AlphaNumeric` plusieurs valeurs.

### <a name="syntax-example-4"></a>Exemple de syntaxe 4

> \<Ajoutez une clé> :: = [**ForceRemove** | **NoRemove** | **Val**]\<nom de clé>

spécifie que `Add Key` équivaut à `Key Name`, et que les littéraux de chaîne, `ForceRemove`, `NoRemove` et `val` sont facultatifs.

### <a name="syntax-example-5"></a>Exemple de syntaxe 5

> \<Alphanumérique> :: = *n’importe quel caractère non null, autrement dit, ASCII 0*

spécifie que `AlphaNumeric` équivaut à n’importe quel caractère non NULL.

### <a name="syntax-example-6"></a>Exemple de syntaxe 6

```rgs
val 'testmulti' = m 'String 1\0String 2\0'
```

spécifie que le nom de clé `testmulti` est une valeur multichaîne composée de `String 1` et de `String 2`.

### <a name="syntax-example-7"></a>Exemple de syntaxe 7

```rgs
val 'testhex' = d '&H55'
```

spécifie que le nom de clé `testhex` est une valeur DWORD définie sur 55 en hexadécimal (85 en décimal). Notez que ce format respecte la notation **&H** qui est celle de la spécification Visual Basic.

## <a name="see-also"></a>Voir aussi

[Création de scripts d’inscription](../atl/creating-registrar-scripts.md)
