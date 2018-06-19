---
title: _lsearch_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _lsearch_s
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _lsearch_s
- lsearch_s
dev_langs:
- C++
helpviewer_keywords:
- linear searching
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- searching, linear
- _lsearch_s function
- lsearch_s function
ms.assetid: d2db0635-be7a-4799-8660-255f14450882
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 12315350b62673abb0a838f9d30830354c58da73
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404196"
---
# <a name="lsearchs"></a>_lsearch_s

Effectue une recherche linéaire portant sur une valeur. Version de [_lsearch](lsearch.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
void *_lsearch_s(
   const void *key,
   void *base,
   unsigned int *num,
   size_t size,
   int (__cdecl *compare)(void *, const void *, const void *),
   void * context
);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Objet à rechercher.

*base*<br/>
Pointeur désignant la base du tableau à explorer.

*Nombre*<br/>
Nombre d'éléments.

*size*<br/>
Taille de chaque élément de tableau en octets.

*compare*<br/>
Pointeur désignant la routine de comparaison. Le deuxième paramètre est un pointeur désignant la clé pour la recherche. Le troisième paramètre est un pointeur désignant un élément de tableau à comparer à la clé.

*Contexte*<br/>
Pointeur désignant un objet accessible dans la fonction de comparaison.

## <a name="return-value"></a>Valeur de retour

Si *clé* est trouvé, **_lsearch_s** retourne un pointeur vers l’élément du tableau à *base* qui correspond à *clé*. Si *clé* n’est trouvé, **_lsearch_s** retourne un pointeur vers l’élément qui vient d’être ajouté à la fin du tableau.

Si des paramètres non valides sont passés à la fonction, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, puis **errno** a la valeur **EINVAL** et la fonction retourne **NULL**. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Conditions d’erreur

|*key*|*base*|*compare*|*Nombre*|*size*|**errno**|
|-----------|------------|---------------|-----------|------------|-------------|
|**NULL**|any|any|any|any|**EINVAL**|
|any|**NULL**|any|!= 0|any|**EINVAL**|
|any|any|any|any|zéro|**EINVAL**|
|any|any|**NULL**|an|any|**EINVAL**|

## <a name="remarks"></a>Notes

Le **_lsearch_s** fonction effectue une recherche linéaire pour la valeur *clé* dans un tableau de *nombre* éléments, chacun des *largeur* octets. Contrairement aux **bsearch_s**, **_lsearch_s** ne nécessite pas de tableau à trier. Si *clé* n’est trouvé, puis **_lsearch_s** ajoute à la fin du tableau et incrémente *nombre*.

Le *comparer* fonction est un pointeur vers une routine fournie par l’utilisateur qui compare deux éléments du tableau et retourne une valeur précisant leur relation. Le *comparer* fonction prend également le pointeur vers le contexte comme premier argument. **_lsearch_s** appelle *comparer* une ou plusieurs fois lors de la recherche, le passage de pointeurs vers deux éléments de tableau à chaque appel. *comparer* doit comparer les éléments et puis retourner soit différente de zéro (ce qui signifie que les éléments sont différents), ou 0 (ce qui signifie que les éléments sont identiques).

Le *contexte* pointeur peut être utile si la structure de données de recherche fait partie d’un objet et le *comparer* fonction a besoin d’accéder aux membres de l’objet. Par exemple, le code dans le *comparer* fonction peut effectuer un cast du pointeur void dans les membres de type et l’accès de l’objet approprié de cet objet. L’ajout de la *contexte* pointeur rend **_lsearch_s** plus sécurisé car un contexte supplémentaire peut être utilisé pour éviter les bogues de réentrance associés à l’utilisation de variables statiques pour ces données à la *comparer* (fonction).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_lsearch_s**|\<search.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Recherche et tri](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[_lsearch](lsearch.md)<br/>
