Implementasi Turicreate's ItemContentRecommender pada dataset Ponpare's Coupon Purchase Prediction  
Private : 0.00636  
Public : 0.00855  

## Requirements
Ubuntu 18.04 64bit (Windows tidak supported, terakhir coba di 20.04 masih gak support)  

Python 3.7.6 (3.5 hingga 3.7)  

turicreate==6.2.1    
pandas==1.0.3  
numpy==1.18.2  
kaggle==1.5.6 opsional  

## Dataset
Masukkan dataset CouponPP kedalam folder dataset  

Dataset dapat diakses dari link berikut  
https://www.kaggle.com/c/coupon-purchase-prediction/data  

Dataset yang terpakai hanya:  
1. coupon_detail_train.csv  
2. coupon_list_test.csv  
3. coupon_list_train.csv  
4. coupon_visit_train.csv  
5. sample_submission.csv  
6. user_list.csv  

## How to run
Run CPP_turi.ipynb via notebook atau ipython.  

Pickled model akan tersimpan di folder model dengan nama Turi_ItemContentRec_Model.mdl  
File submission tersimpan di folder submission dengan nama sub_CPP_turi_ItemContentRec_[waktu_pembuatan].csv  

Jika ada API Kaggle, submission akan dikirim secara langsung dan script akan mencoba menarik hasil submission dengan batas waktu 3 menit.  

## Author's last run
Dengan Ryzen 5 3600 12 threads + 16GB RAM, runtime 1 menit 46 detik (termasuk durasi submit ke kaggle)  
MAP@10 Kaggle  
Private : 0.00636  
Public : 0.00855  

## Main Point
turicreate.recommender.item_content_recommender.create(item_data=item_data, observation_data=observation_data, item_id='COUPON_ID_hash', user_id='USER_ID_hash', target='PURCHASE_COUNT')  
item_data : SFrame berisi detail item  
observation_data : SFrame berisi relasi user-item dengan score/rating  
item_id : ID item pada item_data dan observation_data  
user_id : ID user pada observation_data  
target : fitur target (score/rating) pada observation_data  

model.recommend(users=users, k=len(cl_test), items=items)  
users = SFrame berisi list ID user  
k = jumlah item yang ingin direkomendasikan (Karena kita mau beri bonus skor kepada visited coupon, isi dengan jumlah coupon test)  
items = SFrame berisi list ID item  
