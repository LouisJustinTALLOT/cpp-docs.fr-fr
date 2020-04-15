---
title: _lsearch_s
ms.date: 4/2/2020
api_name:
- _lsearch_s
- _o__lsearch_s
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _lsearch_s
- lsearch_s
helpviewer_keywords:
- linear searching
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- searching, linear
- _lsearch_s function
- lsearch_s function
ms.assetid: d2db0635-be7a-4799-8660-255f14450882
ms.openlocfilehash: 720b83dd48b42d77f35bce12f16e8ac79eb3b4d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341647"
---
# <a name="_lsearch_s"></a>_lsearch_s

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

*nombre*<br/>
Nombre d'éléments.

*Taille*<br/>
Taille de chaque élément de tableau en octets.

*Comparer*<br/>
Pointeur désignant la routine de comparaison. Le deuxième paramètre est un pointeur désignant la clé pour la recherche. Le troisième paramètre est un pointeur désignant un élément de tableau à comparer à la clé.

*context*<br/>
Pointeur désignant un objet accessible dans la fonction de comparaison.

## <a name="return-value"></a>Valeur de retour

Si *la clé* est trouvée, **_lsearch_s** renvoie un pointeur à l’élément du tableau à la *base* qui correspond à *la clé*. Si *la clé* n’est pas trouvée, **_lsearch_s** renvoie un pointeur à l’élément nouvellement ajouté à la fin du tableau.

Si des paramètres non valides sont passés à la fonction, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, alors **errno** est réglé à **EINVAL** et la fonction retourne **NULL**. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Conditions d'erreur

|*key*|*base*|*Comparer*|*nombre*|*Taille*|**errno**|
|-----------|------------|---------------|-----------|------------|-------------|
|**Null**|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|**EINVAL (EN)**|
|n'importe laquelle|**Null**|n'importe laquelle|!= 0|n'importe laquelle|**EINVAL (EN)**|
|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|zéro|**EINVAL (EN)**|
|n'importe laquelle|n'importe laquelle|**Null**|an|n'importe laquelle|**EINVAL (EN)**|

## <a name="remarks"></a>Notes

La fonction **_lsearch_s** effectue une recherche linéaire de la *clé* de valeur dans un tableau d’éléments de *nombre,* chacun des octets de *largeur.* Contrairement à **bsearch_s,** **_lsearch_s** n’exige pas que le tableau soit trié. Si *la clé* n’est pas trouvée, alors **_lsearch_s** l’ajoute à la fin du tableau et le *nombre*d’incréments .

La fonction *de comparaison* est un pointeur à une routine fournie par l’utilisateur qui compare deux éléments de tableau et retourne une valeur spécifiant leur relation. La fonction *de comparaison* prend également le pointeur au contexte comme premier argument. **_lsearch_s** appels *se comparent* une ou plusieurs fois au cours de la recherche, passant des pointeurs à deux éléments de tableau sur chaque appel. *comparer* doit comparer les éléments, puis retourner soit nonzero (ce qui signifie que les éléments sont différents) ou 0 (ce qui signifie que les éléments sont identiques).

Le pointeur *de contexte* peut être utile si la structure de données recherchée fait partie d’un objet et que la fonction *de comparaison* doit accéder aux membres de l’objet. Par exemple, le code de la fonction *de comparaison* peut jeter le pointeur vide dans le type d’objet approprié et accéder aux membres de cet objet. L’ajout *du* pointeur contextuelle rend **_lsearch_s** plus sûr parce que le contexte supplémentaire peut être utilisé pour éviter les bogues de réenterrabilité associés à l’utilisation de variables statiques pour rendre les données disponibles à la fonction *de comparaison.*

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_lsearch_s**|\<search.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Recherche et tri](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[_lsearch](lsearch.md)<br/>
