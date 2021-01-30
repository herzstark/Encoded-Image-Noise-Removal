clear, clc;
Encoded=imread('EncodedImage.png');
subplot(1,2,1),imshow(Encoded),title('Encoded');
prob1=zeros(256,1);
prob2=zeros(256,1);
occurance=zeros(256,1);
output=zeros(256,1);
cumul=zeros(256,1);
sum=0 ;
decoded=uint8(zeros(size(Encoded,1),size(Encoded,2)));
pix_num=size(Encoded,1)*size(Encoded,2);
%%first I need to count the every pixel in the picture and store the number
%%of it into an array
for i = 1:1:size(Encoded,1)
    for j = 1:1:size(Encoded,2)
        pixval=Encoded(i,j);
        occurance(pixval+1)=occurance(pixval+1)+1; %% here we store pixels to occurance
        prob1(pixval+1)=occurance(pixval+1)/pix_num; %%found the probability % of the pixels and stored it to prob1
    end
end
%%here I have to find the cumulative probability
white=255;
for i=1:1:size(prob1)
    sum=sum+occurance(i);%%for every probability I am increasing sum with next occurance to get cumulative
    cumul(i)=sum; 
    prob2(i)=cumul(i)/pix_num;%%I found the cumulative probability here for every intensity
    output(i)=round(prob2(i)*white); %%I round the number here because I don't want it to be fractional
end

for i=1:1:size(Encoded,1)
    for j=1:1:size(Encoded,2)
        decoded(i,j)=output(Encoded(i,j)+1);%%created new image
    end
end
subplot(1,2,2),imshow(decoded),title('Decoded');
imwrite(decoded,'DecodedImage.png');
