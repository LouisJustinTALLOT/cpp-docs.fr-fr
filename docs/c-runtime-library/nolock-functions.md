---
title: Fonctions _nolock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- _nolock functions
- nolock functions
ms.assetid: 7d651d87-38d2-4303-9897-fdb5f7a3e899
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5dca9fa9e0708e1fa8562fe2188362ac73c9be4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391572"
---
# <a name="nolock-functions"></a>_nolock, fonctions

Ce sont des fonctions qui n’effectuent pas de verrouillage. Elles sont fournies pour les utilisateurs nécessitant des performances maximales. Pour plus d'informations, consultez [Performances des bibliothèques multithreads](../c-runtime-library/multithreaded-libraries-performance.md).

 Utilisez les fonctions _nolock uniquement si votre programme est réellement monothread, ou s’il effectue son propre verrouillage.

## <a name="no-lock-routines"></a>Aucune routine de verrouillage

 [_fclose_nolock](../c-runtime-library/reference/fclose-nolock.md)

 [_fflush_nolock](../c-runtime-library/reference/fflush-nolock.md)

 [_fgetc_nolock, _fgetwc_nolock](../c-runtime-library/reference/fgetc-nolock-fgetwc-nolock.md)

 [_fread_nolock](../c-runtime-library/reference/fread-nolock.md)

 [_fseek_nolock, _fseeki64_nolock](../c-runtime-library/reference/fseek-nolock-fseeki64-nolock.md)

 [_ftell_nolock, _ftelli64_nolock](../c-runtime-library/reference/ftell-nolock-ftelli64-nolock.md)

 [_fwrite_nolock](../c-runtime-library/reference/fwrite-nolock.md)

 [_getc_nolock, _getwc_nolock](../c-runtime-library/reference/getc-nolock-getwc-nolock.md)

 [_getch_nolock, _getwch_nolock](../c-runtime-library/reference/getch-nolock-getwch-nolock.md)

 [_getchar_nolock, _getwchar_nolock](../c-runtime-library/reference/getchar-nolock-getwchar-nolock.md)

 [_getche_nolock, _getwche_nolock](../c-runtime-library/reference/getche-nolock-getwche-nolock.md)

 [_getdcwd_nolock, _wgetdcwd_nolock](../c-runtime-library/reference/getdcwd-nolock-wgetdcwd-nolock.md)

 [_putc_nolock, _putwc_nolock](../c-runtime-library/reference/putc-nolock-putwc-nolock.md)

 [_putch_nolock, _putwch_nolock](../c-runtime-library/reference/putch-nolock-putwch-nolock.md)

 [_putchar_nolock, _putwchar_nolock](../c-runtime-library/reference/putchar-nolock-putwchar-nolock.md)

 [_ungetc_nolock, _ungetwc_nolock](../c-runtime-library/reference/ungetc-nolock-ungetwc-nolock.md)

 [_ungetch_nolock, _ungetwch_nolock](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)

## <a name="see-also"></a>Voir aussi

[Entrée et sortie](../c-runtime-library/input-and-output.md)<br/>
 [Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
