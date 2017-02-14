* DEMO1 
 - scan the article QR-CODE (That contains a transaction_id)
 - getArticleTravel(transaction_id)
 - display various transactions using GMAPS

* DEMO2 
 - Scan with the buyer the seller article QR-CODE (That contains a transaction_id)
 - given t = getTransaction(transaction_id) use addTransaction(article_id = t.article_id, 
                                                               seller_id = t.buyer_id, 
                                                               buyer_id  = current_user_id)
 - t1 = getTransaction(article_id,buyer_id)
 - display the new path with getArticleTravel(t1.transaction_id) 
