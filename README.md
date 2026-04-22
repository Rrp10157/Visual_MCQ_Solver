 This is a Google Colab notebook that uses Vision Language Models (VLMs) to automatically  
  solve multiple-choice questions (MCQs) from PNG images. It implements two independent     
  pipelines:                                                                                
                                                                                            
  ---
  Pipeline 1 — Microsoft Phi-3.5-Vision (Cells 1–12)                                        
                                                                                            
  - Model: microsoft/Phi-3.5-vision-instruct (~8 GB VRAM, requires T4 GPU)
  - Execution results: Ran on 17 images, produced submission.csv                            
    - Distribution: A=11, B=4, D=2                                                          
  - Includes compatibility patches for transformers >= 4.43 (DynamicCache.seen_tokens issue)
  - Uses greedy decoding (do_sample=False) for deterministic answers                        
  - Optional majority voting (Cell 12) with temperature sampling for higher accuracy
                                                                                            
  Pipeline 2 — Qwen2-VL-2B-Instruct (Cells Q1–Q12)                                          
                                                                                            
  - Model: Qwen/Qwen2-VL-2B-Instruct (~4.4 GB VRAM, faster/lighter)                         
  - Execution results: Ran on 7 images, produced submission_qwen.csv
    - Distribution: A=1, B=6                                                                
  - No compatibility patches needed
  - Uses qwen_vl_utils.process_vision_info for image preprocessing                          
  - Also supports majority voting (Cell Q12)                                                
                                                                                            
  ---                                                                                       
  Common Features                                                                           
                  
  - Image source: Upload manually (file picker) or via ZIP
  - Output: submission.csv / submission_qwen.csv with columns id, answer                    
  - Optional evaluation: Upload ground_truth.csv to compute accuracy                        
  - Model caching: Saves to Google Drive to avoid re-downloading each session               
  - Prompt strategy: System prompt framing the model as a "deep learning professor", asking 
  for only a single letter A/B/C/D                                                          
                                                                                            
  Both models had their downloaded weights cached in /content/drive/MyDrive/models/ and were
   already present when the notebook ran.
