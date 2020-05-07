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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: d8c421eb3c7a6a617ce073cbf5f36416294c1874
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920448"
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

*number*<br/>
Nombre d'éléments.

*size*<br/>
Taille de chaque élément de tableau en octets.

*compar*<br/>
Pointeur désignant la routine de comparaison. Le deuxième paramètre est un pointeur désignant la clé pour la recherche. Le troisième paramètre est un pointeur désignant un élément de tableau à comparer à la clé.

*context*<br/>
Pointeur désignant un objet accessible dans la fonction de comparaison.

## <a name="return-value"></a>Valeur de retour

Si la *clé* est trouvée, **_lsearch_s** retourne un pointeur vers l’élément du tableau au niveau de *base* qui correspond à la *clé*. Si la *clé* est introuvable, **_lsearch_s** retourne un pointeur vers l’élément qui vient d’être ajouté à la fin du tableau.

Si des paramètres non valides sont passés à la fonction, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne la **valeur null**. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Conditions d'erreur

|*key*|*base*|*compar*|*number*|*size*|**errno**|
|-----------|------------|---------------|-----------|------------|-------------|
|**NUL**|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|**EINVAL**|
|n'importe laquelle|**NUL**|n'importe laquelle|!= 0|n'importe laquelle|**EINVAL**|
|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|zéro|**EINVAL**|
|n'importe laquelle|n'importe laquelle|**NUL**|an|n'importe laquelle|**EINVAL**|

## <a name="remarks"></a>Notes 

La fonction **_lsearch_s** effectue une recherche linéaire sur la *clé* de valeur dans un tableau d’éléments *Number* , chacun d’octets de *largeur* . Contrairement à **bsearch_s**, **_lsearch_s** ne nécessite pas le tri du tableau. Si la *clé* est introuvable, **_lsearch_s** l’ajoute à la fin du tableau et incrémente le *nombre*.

La fonction *compare* est un pointeur vers une routine fournie par l’utilisateur qui compare deux éléments de tableau et retourne une valeur spécifiant leur relation. La fonction *compare* prend également le pointeur vers le contexte comme premier argument. les appels **_lsearch_s** sont *comparés* une ou plusieurs fois pendant la recherche, en passant des pointeurs à deux éléments de tableau à chaque appel. *compare* doit comparer les éléments, puis retourner une valeur différente de zéro (ce qui signifie que les éléments sont différents) ou 0 (ce qui signifie que les éléments sont identiques).

Le pointeur de *contexte* peut être utile si la structure de données recherchée fait partie d’un objet et que la fonction de *comparaison* doit accéder aux membres de l’objet. Par exemple, le code de la fonction *compare* peut effectuer un cast du pointeur void vers le type d’objet approprié et accéder aux membres de cet objet. L’ajout du pointeur de *contexte* rend **_lsearch_s** plus sécurisé, car un contexte supplémentaire peut être utilisé pour éviter les bogues de réentrance associés à l’utilisation de variables statiques pour rendre les données disponibles pour la fonction de *comparaison* .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

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
