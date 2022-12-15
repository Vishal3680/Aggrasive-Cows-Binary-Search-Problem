# Aggrasive-Cows-Binary-Search-Problem
bool isPossible(vector<int> &stalls, int k , int mid){
    int CowCount = 1;
    int lastPos = stalls[0];
    for(int i = 0 ; i< stalls.size(); i++){
        if(stalls[i]-lastPos >= mid){
            CowCount++;
            if(CowCount == k){
                return true;
             }
            lastPos = stalls[i];
        }
    }
    return false;
}

int aggressiveCows(vector<int> &stalls, int k)    
{
    //    Write your code here.
    int ans = -1;
    sort(stalls.begin(),stalls.end());
    int s = 0;
    int maxi = -1;
    for(int i = 0 ; i<stalls.size() ; i++){
        maxi = max(maxi,stalls[i]);
    }
    int e = maxi;
    while(s<=e){
        int mid = s + ( e - s)/2;
        if(isPossible(stalls,k,mid)){
            ans = mid ;
            s = mid + 1;
        }else{
            e = mid -1;
        }
    }
    return ans;
}
