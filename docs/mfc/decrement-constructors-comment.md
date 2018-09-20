---
title: --Constructors, commentaire | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constructors comment
- declarations, constructors
- MFC source files, Constructors comment
- declaring constructors, code comments
- comments, MFC
- comments, constructors comment
- constructors [MFC], declaring
- instance constructors, code comments
ms.assetid: f400774e-ba85-49ed-85b7-70ef2f7dcb2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f03a65c3f870b1e7648f03b70efe7242c35a21f9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429354"
---
# <a name="-constructors-comment"></a>// Constructeurs, commentaire

La `// Constructors` section d’une déclaration de classe MFC déclare des constructeurs (dans le sens C++), ainsi que toutes les fonctions d’initialisation requises pour utiliser réellement l’objet. Par exemple, `CWnd::Create` est dans la section de constructeurs car avant d’utiliser le `CWnd` de l’objet, il doit être « entièrement construit » en appelant tout d’abord le constructeur C++, puis le `Create` (fonction). En règle générale, ces membres sont publics.

Par exemple, la classe `CStdioFile` a trois constructeurs, un d'entre eux est indiqué dans la liste sous [un exemple des commentaires](../mfc/an-example-of-the-comments.md).

## <a name="see-also"></a>Voir aussi

[Utilisation des fichiers sources MFC](../mfc/using-the-mfc-source-files.md)<br/>
[Commentaire sur l’implémentation](../mfc/decrement-implementation-comment.md)<br/>
[Commentaire d’attributs](../mfc/decrement-attributes-comment.md)<br/>
[Commentaire d’opérations](../mfc/decrement-operations-comment.md)<br/>
[Remplaçable (commentaire)](../mfc/decrement-overridables-comment.md)

