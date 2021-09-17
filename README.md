# Pearson-Correlation-Matrix-Construction
clear all
clear
clc
%%input data
X = [0.948	22.31	0.735	8.92	4.98	29.3	50.3	1.03	28	315.06	9.5;
0.942	23.29	0.752	8.38	4.87	20.9	46.7	0.89	30.5	302.12	8.9;
0.914	21.44	0.685	7.69	3.69	26.5	43.5	1.49	36	325.15	2.7];
%The corresponding data labels
labels = ["Voc",'Jsc','FF',	'\mu h','\mu e','CCL (pi)',	'CCL(lamellar)','RMS','Domain Size','\tau ave','COS'];
X_cor = corr(X,'type','Pearson'); 
X_cor = triu(X_cor);
X_cor(X_cor==0) = nan;
%draw the picture 1
contourf(X_cor);
%set color styles(jet,hsv,hot,cold,etc.)
colormap(jet);
set(gca,'xtick',0:1:20);set(gca,'ytick',0:1:20);
grid on; axis equal;
set(gca,'XTickLabel',labels,'XTickLabelRotation',45,'fontsize',10.5, 'fontname','Times New Roman');
set(gca,'YTickLabel',labels,'YTickLabelRotation',45,'fontsize',10.5, 'fontname','Times New Roman');
figure
%draw the picture 2
h=bar3(X_cor,0.5);
for n=1:numel(h)
    zdata = get(h(n),'ZData');
    set(h(n),'CData',zdata);
    set(h(n),'Facecolor','interp');
end 
caxis([-1 1]);
%set color styles(jet,hsv,hot,cold,bone,etc.)
colormap(bone);
set(gca,'XTickLabel',labels,'XTickLabelRotation',135,'fontsize',10.5, 'fontname','Times New Roman');
set(gca,'YTickLabel',labels,'YTickLabelRotation',45,'fontsize',10.5, 'fontname','Times New Roman');
grid on; 
